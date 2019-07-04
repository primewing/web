# Prime Wing Website

## New Wordpress Setup
1. Download wordpress latest.tar.gz
1. Unzip to /home/moin/www/primewing
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
    // By Moin: Enabling direct plugin/theme installations from admin ui
    // Todo: Disable in production if not required
    define('FS_METHOD', 'direct');
    ```
1. Install page builder and widgets bundle plugins. If you get 'The plugin does not have a valid header' error while activating plugins, activate them from main plugins page. Ref: https://wordpress.org/support/topic/the-plugin-does-not-have-a-valid-header-150/
1. Install siteorigin corp theme and activate it.
1. Follow Theme documentation and customize as required. Ref: https://siteorigin.com/corp-documentation/one-page-website/
