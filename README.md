# apache-subdomain
Make a Apache2 subdomain in Linux

## But how?

First move to apache's sites directory
``` 
cd /etc/apache2/sites-available
```
then copy the template file
```
sudo cp 000-default.conf test.example.com.conf
```
Now edit the new config file
```
sudo nano test.example.com.conf
```
Replace the file's content with the following
```
<VirtualHost *:80>
    ServerAdmin your.email@localhost
    ServerName test.example.com
    ServerAlias www.test.example.com
    DocumentRoot /var/www/test.example.com
    <Directory /var/www/test.example.com>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
    <IfModule mod_dir.c>
        DirectoryIndex index.php index.pl index.cgi index.htmt index.xhtml index.htm index.html
    </IfModule>
</VirtualHost>
```
Now enable the new site with this command
```
sudo a2ensite test.example.com
```
Congrats!

#gg
