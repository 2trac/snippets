### basic admin 

````
# reference 
# https://docs.bitnami.com/aws/faq/administration/control-services/

# check status
sudo /opt/bitnami/ctlscript.sh status

# restar/star/stop apache
sudo /opt/bitnami/ctlscript.sh restart apache


````

### proxy reverse 

````
# ----
# edit file and add vhost on end off file / restart service
# example of reverse proxy running local on port 3000
# ----

vim /opt/bitnami/apache/conf/bitnami/bitnami-ssl.conf

<VirtualHost *:443>
    ServerName your_domain.com

    SSLEngine on
    SSLCertificateFile "/opt/bitnami/apache/conf/your_certificate.crt"
    SSLCertificateKeyFile "/opt/bitnami/apache/conf/your_certificate.key"

    ErrorLog "/opt/bitnami/var/log/sub1_error_log"
    CustomLog "/opt/bitnami/var/log/sub1_access_log" common

    ProxyRequests Off
    <Proxy *>
        Order deny,allow
        Allow from all
    </Proxy>
    ProxyPass / https://localhost:3000/
    ProxyPassReverse / https://localhost:3000/
</VirtualHost>

````

