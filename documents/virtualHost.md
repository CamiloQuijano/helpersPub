[`Volver`](../index.html)

# Virtual Host

Agregar a **httpd-vhosts.conf**  
ubicación: C:\wamp64\bin\apache\apache2.4.23\conf\extra

```xml
	<VirtualHost *:80>
		ServerName local.laravel.com
		ServerAlias local.laravel.com
		DocumentRoot C:/wamp64/www/MyWebAppLaravel/public
		<Directory  "C:/wamp64/www/MyWebAppLaravel/public">
			Options +Indexes +Includes +FollowSymLinks +MultiViews
			AllowOverride All
			Require local
		</Directory>
	</VirtualHost>
```

Agregar a **host**
Ubicación: C:\Windows\System32\drivers\etc

```php
	127.0.0.1       local.laravel.com
```


## Virtual Host - Acceder a localhost por IP en red

Se tiene que actualizar la variable Require
```xml
	Require all granted
```
```xml
<VirtualHost *:80>
	ServerName localhost
	DocumentRoot c:/wamp64/www
	<Directory  "c:/wamp64/www/">
		Options +Indexes +Includes +FollowSymLinks +MultiViews
		AllowOverride All
		Require all granted
	</Directory>
</VirtualHost>
```


## VirtualHost SSL 

Habilitar modules **ssl_modules** en apache 

```php
<VirtualHost *:4432>
    ServerAdmin camiloquijano31@hotmail.com
    DocumentRoot "C:/xampp/htdocs/Altactic/web/"
    ServerName local.altactic.com:4432 
    ServerAlias www.local.altactic.com:4432 
    ErrorLog "logs/Altactic.log"
    CustomLog "logs/Altactic.log" common 
	SSLEngine on 
	SSLCertificateFile "conf/ssl.crt/server.crt" 
	SSLCertificateKeyFile "conf/ssl.key/server.key" 
	<Directory "C:/xampp/htdocs/Altactic/web/">
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>
```

## VirtualHost Error 403

Busca en tu httpd.conf un Deny from all y cámbialo a Allow from all
Quizá ese simple cambio lo solucione

```php
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Order deny,allow
    Allow from all
</Directory> 
```


## Instalar certificado de seguridad
###### Tags: `wamp` `ssl`

Instalar un certicado de seguridad web

1. Pegar los certificados en ruta: 
C:\wamp64\bin\apache\apache2.4.23\conf\key

2. Habilitar modulos relacionados a SSL
C:\wamp64\bin\apache\apache2.4.23\conf\httpd.conf
```xml
	LoadModule socache_shmcb_module modules/mod_socache_shmcb.so
	LoadModule ssl_module modules/mod_ssl.so
	Include conf/extra/httpd-ssl.conf
```
3. Configurar el certificados
C:\wamp64\bin\apache\apache2.4.23\conf\extra\httpd-ssl.conf
```xml
	ServerName next-movil-stg.labdigital.internal:443
	ErrorLog "c:/logs/errorD2C.log"
	TransferLog "c:/logs/accessD2C.log"
	SSLCertificateFile "c:/wamp64/bin/apache/apache2.4.23/conf/key/next-movil-stg.labdigital.internal.pem"
	SSLCertificateKeyFile "c:/wamp64/bin/apache/apache2.4.23/conf/key/next-movil-stg.labdigital.internal.key"
	CustomLog "c:/logs/errorD2C.log" \
```

4. Incluir DNS en host
C:\Windows\System32\drivers\etc
```xml
	127.0.0.1       dev.2compra.co
	127.0.0.1       next-movil-stg.labdigital.internal
```
Validar con nslookup y realizar un ping al dns (consola)

5. Reiniciar el apache, se puede desde servicios
6. En visor de eventos -> aplicación, se puede validar posibles errores en el arranque del apache

Ejemplo estructura 
```xml
	<VirtualHost *:443>
		ServerAdmin webmaster@localhost
		DocumentRoot "C:/wamp64/www"
		#ServerName localhost
		#ServerAlias localhost
		ServerName 2compra.co:443
		ServerAlias 2compra.co:443
		#ServerName dev.2compra.co:443
		#ServerAlias dev.2compra.co:443
		#ServerName dev.2compra.co
		#ServerAlias dev.2compra.co
		ErrorLog C:/logs/errorD2C.log
		CustomLog C:/logs/accessD2C.log combined
		SSLEngine on 
		SSLCertificateFile "C:/config/ceropay/next-movil-stg.labdigital.internal.pem" 
		SSLCertificateKeyFile "C:/config/ceropay/next-movil-stg.labdigital.internal.key" 
		<Directory "C:/wamp64/www/">
			AllowOverride All
			Order allow,deny
			Allow from all
		</Directory>
	</VirtualHost>
```


## VirtualHost Default
- [`Linux Default`](virtualhost/LinuxExampleVirtualHost000-default.conf)
- [`Linux Altactic`](virtualhost/LinuxExampleVirtualHostAltactic.conf)
- [`Linux 2Compra`](virtualhost/virtualhost-2compra.conf)
- [`Windows Default`](virtualhost/Windowshttpd-vhosts.conf)