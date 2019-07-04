## Website Setup
1. Download wordpress latest.tar.gz
1. Unzip to /var/www/primewing
1. Setup DB username/password in mysql container
1. Ensure nginx has primewing.conf loaded and pointed to /var/www/primewing
1. Browse http://primewing.test to continue wordpress database setup
1. If you get mysql_connect errors, login into php container and install php mysqli extension
```
docker-php-ext-enable mysqli
docker-php-ext-install mysqli
```
1. Copy wp-config content from wordpress setup to wp-config.php file
1. Give wp-content ownership permissions to www-data
    ```
    chown -R www-data:www-data wp-content
    ```
1. Enable direct plugin/theme installations from admin ui by adding below config to wp-config.php
    ```
    // Disable in production if not required
    define('FS_METHOD', 'direct');
    ```
1. Install plugins and themes
