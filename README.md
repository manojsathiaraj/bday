vim /etc/apache2/apache2.conf

ServerName localhost
<virtualhost 178.79.157.218:80>
DocumentRoot /var/www/html/bday
customlog /var/log/apache2/httpd_logs common
RewriteEngine On
RewriteCond %{HTTPS} on
RewriteRule (.*) http://%{HTTP_HOST}%{REQUEST_URI}
</virtualhost>

a2enmod rewrite
apache2ctl configtest
systemctl restart apache2
