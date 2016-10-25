# apache_conf


<VirtualHost *:80>
        ServerName %0
        ServerAlias *.%0

        UseCanonicalName Off
        VirtualDocumentRoot /var/web/%0


        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory "/var/web/*">
                Options Indexes FollowSymLinks
                AllowOverride All

                Require all granted
        </Directory>


        ErrorLog /var/web/error.log

        # Possible values include: debug, info, notice, warn, error, crit, alert, emerg.
        LogLevel warn
        CustomLog /var/web/access.log combined

        #LogFormat "%V %h %l %u %t \"%r\" %s %b" vcommon
        #CustomLog /var/web/other_vhosts_access.log vcommon
</VirtualHost>
