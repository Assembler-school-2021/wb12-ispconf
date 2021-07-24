# wb12-ispconf

> Pregunta 1 : configura un htpassword delante el acceso al phpmyadmin
```
apt install apache2-utils
```
Creamos el usuario y su clave:
```
htpasswd -c /etc/nginx/.htpasswd phpmyadmin
```
> Pregunta 1 : configura un htpassword delante el acceso al phpmyadmin
Modificamos el fichero de nginx */etc/nginx/sites-enabled/000-apps.vhost* y añadimos lo siguiente a la sección de location /phpmyadmin
```
  auth_basic           “Phpmyadmin”;
           auth_basic_user_file /etc/nginx/.htpasswd;
```
Y reinciamos nginx;

> Pregunta 2 : configura un nuevo cliente con un nuevo subdominio para el. Cuando lo tengas habilita un accesso ftp y crea una base de datos. Sube una instalación de wordpress y comprueba que todo funciona.

Creamos ftp_client
Creamos el ftp_clientftp_user.
![image](https://user-images.githubusercontent.com/65896169/126865060-4e8822e0-eb4c-487a-9d8e-65b891e9d236.png)


Usamos un cliente FTP para subir la instalación de wp.
![image](https://user-images.githubusercontent.com/65896169/126865064-cdeee522-13b6-4269-9bc7-a8162761ea07.png)


Creamos la bdd, primero el usuario:
![image](https://user-images.githubusercontent.com/65896169/126865067-6396e705-fc7b-469a-9626-49a61c681fa8.png)

![image](https://user-images.githubusercontent.com/65896169/126865073-74a92b24-b517-4bfd-9474-3c2c70b1303b.png)

Y ya podemos empezar la instalación:

![image](https://user-images.githubusercontent.com/65896169/126865077-52ab1615-3a46-44da-adb0-773ab179bdaf.png)

![image](https://user-images.githubusercontent.com/65896169/126865085-3a31eacc-8dbc-4f65-89f9-a97e5ecb6b71.png)


> Pregunta 3 : instala el server de sury de php y instala las versiones 7.1 y 7.2 de fpm. Crea un nuevo site que utilize una de ellas en el isp.

```
apt-get install -y apt-transport-https lsb-release ca-certificates
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
```
PHP 7.1:
```
apt-get install php7.1 php7.1-cli php7.1-cgi php7.1-fpm php7.1-gd php7.1-mysql php7.1-imap php7.1-curl php7.1-intl php7.1-pspell php7.1-recode php7.1-sqlite3 php7.1-tidy php7.1-xmlrpc php7.1-xsl php7.1-zip php7.1-mbstring php7.1-soap php7.1-opcache php7.1-common php7.1-json php7.1-readline php7.1-xml
```
PHP 7.2:
```
apt-get install php7.2 php7.2-cli php7.2-cgi php7.2-fpm php7.2-gd php7.2-mysql php7.2-imap php7.2-curl php7.2-intl php7.2-pspell php7.2-recode php7.2-sqlite3 php7.2-tidy php7.2-xmlrpc php7.2-xsl php7.2-zip php7.2-mbstring php7.2-soap php7.2-opcache php7.2-common php7.2-json php7.2-readline php7.2-xml
```

Y configuramos las nuevas versiones en ISPconf


![image](https://user-images.githubusercontent.com/65896169/126865562-7fbcbf81-dbfb-4d82-b0b0-b8054b35c96f.png)
![image](https://user-images.githubusercontent.com/65896169/126865660-b2a63542-33ab-4d34-a9e4-75a4821ed68f.png)

