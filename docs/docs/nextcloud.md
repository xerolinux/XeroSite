---
title: NextCloud Setup
tags:
  - Linux
  - NextCloud
  - Guide
---

# Installing Nextcloud on Debian VPS

## After Debian Install

1. **Install Necessary Packages:**

    ```shell
    sudo apt install -y exa micro neofetch zram-tools wget unzip curl
    ```

2. **Change zram Configuration:**

    ```shell
    sudo micro /etc/default/zramswap
    ```

3. **Replace `.bashrc`:**

    ```shell
    rm .bashrc
    wget https://raw.githubusercontent.com/drewgrif/dotfiles/main/.bashrc
    bash
    ```

### Installing Nextcloud

1. **Download Nextcloud:**

    ```shell
    wget https://download.nextcloud.com/server/releases/latest.zip
    ```

2. **Install MariaDB:**

    ```shell
    sudo apt install -y mariadb-server
    sudo mysql_secure_installation
    ```

3. **Create Nextcloud Database:**

    ```shell
    sudo mariadb
    ```

    Inside the MariaDB shell:

    ```sql
    CREATE DATABASE nextcloud;
    GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'localhost' IDENTIFIED BY 'mypassword';
    FLUSH PRIVILEGES;
    ```

    Exit the MariaDB shell with `CTRL+D`.

4. **Set Up Apache Webserver:**

    - **Install Required Packages:**

        ```shell
        sudo apt install php php-apcu php-bcmath php-cli php-common php-curl php-gd php-gmp php-imagick php-intl php-mbstring php-mysql php-zip php-xml
        ```

    - **Enable Apache Modules:**

        ```shell
        sudo a2enmod dir env headers mime rewrite ssl
        sudo phpenmod bcmath gmp imagick intl
        ```

    - **Unzip and Move Nextcloud:**

        ```shell
        unzip latest.zip
        sudo chown -R www-data:www-data nextcloud
        sudo mv nextcloud /var/www
        sudo a2dissite 000-default.conf
        ```

    - **Configure Apache for Nextcloud:**

        ```shell
        sudo micro /etc/apache2/sites-available/nextcloud.conf
        ```

        Add the following contents to `nextcloud.conf`:

        ```apache
        <VirtualHost *:80>
            DocumentRoot "/var/www/nextcloud"
            ServerName nextcloud

            <Directory "/var/www/nextcloud/">
                Options MultiViews FollowSymlinks
                AllowOverride All
                Order allow,deny
                Allow from all
            </Directory>

            TransferLog /var/log/apache2/nextcloud_access.log
            ErrorLog /var/log/apache2/nextcloud_error.log
        </VirtualHost>
        ```

    - **Enable Nextcloud Site and Restart Apache:**

        ```shell
        sudo a2ensite nextcloud.conf
        sudo systemctl restart apache2
        ```

5. **Adjust PHP Settings (for Debian 12):**

    ```shell
    sudo micro /etc/php/8.2/apache2/php.ini
    ```

    Update the following parameters:

    ```ini
    memory_limit = 512M
    upload_max_filesize = 16G
    max_execution_time = 360
    post_max_size = 16G
    date.timezone = America/New_York
    opcache.enable=1
    opcache.interned_strings_buffer=32
    opcache.max_accelerated_files=10000
    opcache.memory_consumption=128
    opcache.save_comments=1
    opcache.revalidate_freq=1
    ```

6. **Restart Apache:**

    ```shell
    sudo systemctl restart apache2
    ```

### Dealing with Warnings

1. **Change config.php permissions**

	```bash
	sudo chmod 660 /var/www/my.justaguylinux.cloud/config/config.php
	```

2. **Detected some missing optional indices.**

	Make occ executable: 
	
	```bash
	sudo chmod +x /var/www/my.justaguylinux.cloud/occ
	```
	
	Then add missing indices:
	
	```bash
	sudo /var/www/my.justaguylinux.cloud/occ db:add-missing-indices
	```
	
	Check to see if error is no longer
	
3. **One or more mimetype migrations are available**

	```bash
	sudo /var/www/my.justaguylinux.cloud/occ maintenance:repair --include-expensive
	```
	
4.  **The following warnings**
	
	- Server has no maintenance window start time configured.

	- The database is used for transactional file locking.

	- No memory cache has been configured.

	- Your installation has no default phone region set.

	- You have not set or verified your email server configuration yet.
	
	```bash
	sudo nano /var/www/my.justaguylinux.cloud/config/config.php
	```
	**Remove:** `maintenance => false,`
	
	**Add:**
	
	```php
    'mail_from_address' => 'nextcloud',
	'mail_smtpmode' => 'smtp',
	'mail_sendmailmode' => 'smtp',
	'mail_domain' => 'gmail.com',
	'mail_smtphost' => 'smtp.gmail.com',
	'mail_smtpport' => '587',
	'mail_smtpauth' => 1,
	'mail_smtpname' => 'nextcloud@gmail.com',
	'mail_smtppassword' => 'app-specific-pw',
	'maintenance_window_start' => 1,
	'memcache.local' => '\\OC\\Memcache\\APCu',
	'memcache.distributed' => '\\OC\\Memcache\\Redis',
	'memcache.locking' => '\\OC\\Memcache\\Redis',
	'redis' => 
	array (
	'host' => 'localhost',
	'port' => 6379,
	),
	'default_phone_region' => 'US',
	'overwriteprotocol' => 'https',
	```

5. **Some headers are not set correctly on your instance - The `Strict-Transport-Security` HTTP header is not set (should be at least `15552000` seconds).**

	```bash
	sudo nano /etc/apache2/sites-available/my.justaguylinux.cloud.conf
	```
	
	**Add after </Directory>**
	
	```ini
	<IfModule mod_headers.c>
      Header always set Strict-Transport-Security "max-age=15552000; in>
    </IfModule>
    ```
    **Restart apache2**
    
    ```bash
    sudo systemctl restart apache2
    ```

6. **Array:  Not a warning but good idea**

	```bash
	sudo nano /var/www/my.justaguylinux.cloud/config/config.php
	```

	```bash
		'trusted_domains' => 
		array (
		0 => '192.168.254.80',
		1 => 'venetian',
		2 => 'my.justaguylinux.cloud',
		),
	
	```

---

## Files Drop

Nextcloud Files Drop is a feature designed to simplify the process of receiving files from others, especially when they don't have a Nextcloud account. It allows you to create upload-only links where people can easily upload files to your Nextcloud instance without requiring them to log in or have an account. Here's a more detailed look at Nextcloud Files Drop:

### Key Features

1. **Create Upload Links:**
   - **Generate Links:** You can create a unique upload link for a specific folder in your Nextcloud. This link can be shared with anyone who needs to upload files.
   - **No Account Needed:** The people receiving the link do not need to have a Nextcloud account to upload files.

2. **Manage Upload Permissions:**
   - **Set Folder Limits:** You can designate specific folders for file uploads, keeping your main storage organized and separating uploaded files from other content.
   - **Limit Upload Size:** Control the maximum file size that can be uploaded via the link to prevent excessively large files from being added.

3. **Security and Privacy:**
   - **Expiration Dates:** Set an expiration date for the upload link, ensuring it is only valid for a certain period of time.
   - **Password Protection:** You can add a password to the upload link, adding an extra layer of security to control who can access the link.

4. **Notifications:**
   - **Receive Alerts:** Get notifications when someone uploads a file through the link. This helps you keep track of incoming files and manage them efficiently.

5. **User-Friendly Interface:**
   - **Simple Upload Interface:** The upload page is designed to be straightforward and user-friendly, making it easy for anyone to upload files without needing technical knowledge.

6. **Integration with Nextcloud's File Management:**
   - **Organize Files:** Uploaded files are automatically stored in the designated folder within Nextcloud, making it easy to organize and manage them alongside your other files.

### How to Use Files Drop

1. **Enable Files Drop:**
   - Ensure the Files Drop app is enabled in your Nextcloud instance. This can be done through the Nextcloud App Store or by accessing the Nextcloud app management settings.

2. **Create a Files Drop Link:**
   - Go to the folder where you want to receive files.
   - Click on the "Share" button for that folder.
   - Select the option to create a Files Drop link.

3. **Configure the Link:**
   - Set any desired options such as expiration date, password protection, and file size limits.
   - Copy the generated link.

4. **Share the Link:**
   - Send the link to the individuals who need to upload files. They will be able to use the link to access the upload interface.

5. **Monitor and Manage:**
   - Monitor incoming files and manage them as needed. You can access them in the designated folder and organize them according to your preferences.

### Use Cases for Files Drop

- **Collecting Documents:** Useful for collecting documents from clients, collaborators, or team members without needing them to have a Nextcloud account.
- **Event or Project Contributions:** Ideal for gathering contributions or files related to a specific event or project from multiple people.
- **Public File Requests:** Handy for scenarios where you need to collect files from a large group of people, such as during surveys or feedback collection.

Nextcloud Files Drop streamlines the process of collecting files while maintaining control and organization within your Nextcloud environment. It enhances collaboration and makes file submission straightforward for anyone involved.

---

## Nextcloud App

### File Management

1. **Nextcloud Files**: Powerful, portable cloud storage for uploading, managing, and sharing files with features like advanced sharing options and file versioning.
2. **Files Metadata**: Enhance file organization with rich metadata for easier search and categorization.
3. **External Storage**: Integrate various external storage services to centralize file access.
4. **FileDrop**: Easily share files by dragging and dropping them into a designated area, simplifying file transfer.
5. **Dropbox Integration**: Connect your Dropbox account for seamless access and synchronization of files.

### Communication & Collab
1. **Nextcloud Talk**: Secure video calls, chat, and conferencing to facilitate team communication while prioritizing privacy.
2. **Collabora Online / OnlyOffice**: Collaborative document editing within Nextcloud, allowing real-time teamwork.
3. **Deck**: Visual project management tool for organizing tasks into boards and cards.
4. **Tasks**: Straightforward to-do list manager for tracking tasks and deadlines effectively.
   - 4a. **Integration**: GNOME Endeavour app for enhanced task management.
   - 4b. **Mobile Options**:
     - OpenTasks for Android
     - iOS sync with Apple Reminders
     - Nextcloud Deck for collaborative task management
5. **Collectives**: Collaborative knowledge base to organize and share information within teams.
6. **Element**: A secure chat and collaboration app integrated with Nextcloud for Matrix communication, promoting seamless team interactions.
7. **Repod**: A podcast app for managing and sharing podcast subscriptions, enhancing team engagement through audio content.

### Personal Management
1. **Passwords**: Self-hosted password manager for secure management and sharing of sensitive data.
2. **Contacts**: Manage and securely share contacts with seamless syncing.
3. **Calendar**: Schedule events and share calendars for organized planning.
4. **Notes**: Portable Markdown-based note-taking app for structured documentation.
5. **Google Synchronization App**: Sync your Google Calendar and Contacts with Nextcloud for unified management.

### Media & Content
1. **Nextcloud Photos**: Manage and share your photo collections securely, creating albums and organizing memories.
2. **Nextcloud Maps**: Explore and manage maps, integrating location-based features for enhanced project planning.
3. **News**: RSS feed reader for aggregating content from various sources.
4. **Extract**: A powerful tool for extracting text and images from documents and files for easier data management.

### Surveys and Feedback
1. **Forms**: Create customizable forms and surveys to collect feedback while ensuring user privacy.

### Integration & Customization
1. **Mastodon Integration**: Connect with the decentralized social network for enhanced connectivity.
2. **Twitter Integration**: Seamlessly integrate with Twitter for quick updates and interaction.
3. **Custom Menu**: Tailor the Nextcloud menu for an optimized user experience.
4. **External Sites**: Add links to external websites or applications to create a centralized hub.
5. **Bookmarks**: Save and share favorite websites with integration for the Firefox extension **Floccus** for easy synchronization.
6. **Custom CSS**: Customize the Nextcloud interface with your own CSS styling, enhancing the visual experience and allowing for unique modifications.
7. **Google Docs Redirect App**: Easily redirect to Google Docs from Nextcloud for seamless document access and editing.
8. **LibreSign**: A document signing app that allows you to sign documents securely and manage signatures within Nextcloud.

### Security Features
1. **Two-Factor Authentication**: Add an extra layer of protection during login.

### Productivity Enhancements
1. **Bookmarks**: Organize and access most visited links easily.
2. **Unrounded Corners**: A design feature to enhance the aesthetic appeal of the Nextcloud interface.
3. **Breeze Dark Theme**: A visually appealing dark theme option that can utilize custom CSS styling for further personalization.

## Wrap up

That's it. If you have any additional tips send them my way so I can add to this thing. The more the merrier. Useful for all.
