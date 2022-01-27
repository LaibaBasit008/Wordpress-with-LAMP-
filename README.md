# Wordpress-with-LAMP
<h2>EC2 Instance</h2>
<p>Use main.tf to set up ec2 instance</p>
<h2>LAMP STACK</h2>
<p>Follow this reference to
<a href="https://github.com/LaibaBasit008/Webserver-configuration-using-Terraform">Setup Lamp</a> to the point of installing phpmyadmin</p>
<h2>WordPress Setup</h2>
<p>Follow these commands to setup WordPress</p>
<ul>
<li>sudo mysql -u root
</li>
<p>update the root user’s password</p>
<li>ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'new_password';
</li>
<p>Type Exit</p>
<li>mysql -u root -p
</li>
<li>CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
</li>
<li>CREATE USER 'wordpressuser'@'%' IDENTIFIED WITH mysql_native_password BY 'set_your_own_password';
</li>
<li>GRANT ALL ON wordpress.* TO 'wordpressuser'@'%';
</li>
<li>FLUSH PRIVILEGES;
</li>
<li>EXIT;
</li>
<li>sudo apt update
</li><li>sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip
</li>

<li>sudo systemctl restart apache2
</li>

<li>sudo nano /etc/apache2/sites-available/wordpress.conf
</li>
<p> allow .htaccess files using:</p>

<li><Directory /var/www/wordpress/>
    AllowOverride All
</Directory></li>
<p>Press Ctrl+X to exit along with y</p>
<li>sudo a2enmod rewrite
</li>

<li>sudo apache2ctl configtest
</li>
<li>sudo systemctl restart apache2
</li>
<li>cd /tmp</li><li>
curl -O https://wordpress.org/latest.tar.gz
</li>
<li>tar xzvf latest.tar.gz
</li>
<li>touch /tmp/wordpress/.htaccess
</li>
<li>cp /tmp/wordpress/wp-config-sample.php /tmp/wordpress/wp-config.php
</li>
<li>mkdir /tmp/wordpress/wp-content/upgrade
</li>
<li>sudo cp -a /tmp/wordpress/. /var/www/wordpress
</li>
<li>sudo chown -R www-data:www-data /var/www/wordpress
</li>
<li>sudo find /var/www/wordpress/ -type d -exec chmod 750 {} \;</li><li>
sudo find /var/www/wordpress/ -type f -exec chmod 640 {} \;
</li>
<li>curl -s https://api.wordpress.org/secret-key/1.1/salt/
</li>
<p>Copy these values and run following command</p>
<li>sudo nano /var/www/wordpress/wp-config.php
</li>
<p>Remove these and paste copied values here</p>
<img src="a.PNG"/>
<p>Put database name at DB_NAME and user at DB_USER set while creating wordpress database. Replace DB_collate with define('FS_METHOD', 'direct');</p>
<img src="db.PNG"/>
<p>Refresh Public IP and Install WP</p>



</ul>

<h2>Install WP</h2>
<p>Set Language</p>
<img src="Lang.PNG"/>
<p>Set username, email and password</p>
<img src="wp.PNG"/>
<p>Login using above username and password. Edit Site using dashboard</p>
<img src="dashboard.PNG"/>
<p>Refresh url now it will contain your WP Site</p>
<img src="wps.PNG"/>
