# LEMP STACK DOCUMENTATION
![LEMP STACK](https://github.com/sheezylion/LEMP-STACK/assets/142250556/8f56b168-dd72-4416-9dc7-2e84b29b4fa7)

## WHAT IS LEMP STACK
LEMP is an open source web-application stack used to develop web applications. The term LEMP is an acronym that represents:
- L - Linux operating system
- E - Nginx server (Pronounced as engine-x, hence the E is acronym)
- M - Mysql database
- P - Php for scripting langiage


LEMP enjoys community support, hence it is used around the world in many highly scaled web applications. Nginx is the secind most widely used web server in the world following apache.

## HOW LEMP STACK WORLS
The LEMP stack works by using nginx web server, which listens for HTTP request and forward it to the appropriate php script. The php script generate a response which is then sent back to the user via nginx.
Mysql is used to store and manage the website data. Php communicate with mysql to retrieve and store data as needed.

## WHY LEMP STACK IS POPULAR IN WEB DEVELOPMENT
- High performance 
- Scalability
- Open-source
- Security

## Disaavantages of LEMP
- If configurations are considered Nginx does not allow additional configurations which is a downside unlike Apache as it is more flexible in this case.
- Not flexible enough to support dynamic modules and loading.

## Prerequisites
In order to install nginx web-server, mysql database and php, we need to first launch a server in AWS using EC2 instance.

## How to launch an EC2 instance server on AWS
To get started search EC2 in your AWS console, click on launch instance to create an instance and name the requirement

<img width="1401" alt="1" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/47909bef-7054-4998-b47a-03e3ccf72ca1">

Step 1: Once you click on launch instance, the next thing is to name your server and choose your preferred Amazon machine image AMI, we would select ubuntu 24.04 LTS free tier

<img width="803" alt="2" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/511dcd02-a312-4a22-b622-db95cdb6cdee">

Step 2: Choose instance type, select t2.micro, then select key pair. if you don't have one created before or select an existing one. I have created one before, so i would select it.

<img width="804" alt="3" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/f8a51c81-9b52-4406-b974-d812afe58408">

Step 3: Select create a security group, ssh traffic on port 22 has been allowed by default, you can choose to disallow but in our case we want to ssh into our server from the terminal, so we would allow. Also select allow HTTPS traffic and HTTP traffic from the internet. 

<img width="793" alt="4" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/4936cb06-af95-466e-bff9-effcc3e3143d">

step 4: Check the summary to double check, once satisfied. Click on launch instance

<img width="808" alt="5" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/f757b103-9ddf-49d6-add4-075f31d3adcd">

Once you click on launce instance this should display:

<img width="868" alt="6" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/891037d7-f6ee-428f-8156-d3ae905e5bed">

Your instance is now launched with detailed information of bothe public and private ip-adress

<img width="1419" alt="7" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/043df635-e60d-42a5-ad1f-371c8143c81e">

step 5: Click on security then click on the link under security group. This will allow us to see the inbound rules information and confirm if what we edited in step 3 is valid

<img width="1337" alt="8" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/41a3cec3-4c35-47b2-9e6a-017f1fdff88c">

Step 6: ssh into your terminal using the key pair that was downloaded earlier

```
ssh -i ~/Download/demo-key ubuntu@54.236.4.220
```
The ~/Download is the path where my key pair named demo-key is located. Ubuntu is the username which is followed by @ and the public ip-address 54.236.4.220

<img width="555" alt="9" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/f3cdde45-97c1-454a-8a09-8f67697af688">

### Install nginx into AWS EC2 instance and update firewall
Steps to install nginx

step 1: Update annd upgrade list of packages in package manager

```
sudo apt update 
sudo apt upgrade -y
```
<img width="825" alt="10" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/e5269e7d-1060-4a6a-ad7f-9ae302ccbfb3">

Step 2: Install nginx using the command below

```
sudo apt install nginx 
```
<img width="795" alt="11" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/445148c1-89d9-4f00-914f-9f712a9f5241">

Step 3: Enable nginx and check status to confirm if its running

```
sudo systemctl enable apache2
sudo systemctl status apache2
```
<img width="1006" alt="12" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/c09a15d5-ef1f-40a1-8c1f-914ebb98b5c9">

Step 4: The server is running and can be accessed locally in the ubuntu shell by running the command below:

```
curl http://localhost:80
or
curl http://127.0.0.1:80
```
<img width="586" alt="13" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/6c7c3bec-88b1-4c26-8104-efeac7027a6d">

You can also check through your browser using the public ip-address of our server

```
http://54.236.4.220:80
```
<img width="777" alt="14" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/b491e779-06b8-4f65-b27e-a2923c721781">

Another way to retrieve your public ip-address, other than to check it in the AWS console is to use the following command:

```
curl -s http://169.254.169.254/latest/meta-data/public-ipv4
```
<img width="668" alt="15" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/71259eef-9591-454d-a61f-60f97a302a4b">

### Install Mysql into server
Steps to install mysql server. This steps would let us install, create and change password 

Step 1: Install mysql server

```
sudo apt install mysql-server
```

Step 2: Enable and verify if mysql server is running using the command below

```
sudo systemctl enable mysql
sudo systemctl status mysql
```
<img width="820" alt="16" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/ea0b1659-5598-4f85-be04-a3834a1d4057">

Step 3: Log into mysql-server with the comman  below

```
sudo mysql
```
<img width="576" alt="17" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/7cbf9dd5-3967-4ece-8741-a7f66d1cc6cb">

Step 4: Set a password for root user. The root user password is set to New.1.pass

```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'New.1.pass';
```

Step 5 Type exit, to exit from mysql server

```
exit
```
<img width="699" alt="18" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/717d6932-6f2c-4b7c-8ae3-e64b6a2e0a8e">

Step 6: Run an interactive script using the command below, this script removes some insecure settings and lock down access to the database system.
```
sudo mysql_secure_installation
```
This will ask if you want to configure the VALIDATE PASSWORD PLUGIN. Answer Y for yes, or anything else to continue without enabling.

<img width="638" alt="19" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/33a4270a-986a-465d-92f0-51e74a591fa8">

If you answer “yes”, you’ll be asked to select a level of password validation. Keep in mind that if you enter 2 for the strongest level, you will receive errors when attempting to set any password which does not contain numbers, upper and lowercase letters, and special characters, or which is based on common dictionary words.

<img width="563" alt="20" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/555e3308-0c07-4803-a273-d6ec342f9607">

For the rest of the questions, press Y and hit the ENTER key at each prompt. This will remove some anonymous users and the test database, disable remote root logins, and load these new rules so that MySQL immediately respects the changes you have made.

When you’re finished, test if you’re able to log in to the MySQL console by typing:

```
sudo mysql -p
```
<img width="627" alt="21" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/9d3166b9-8a20-4d42-bd56-f52b854fc18a">

Exit from the server. Mysql server is now installed and secured. 

### Install PHP into AWS EC2 instance

You have Nginx installed to serve your content and MySQL installed to store and manage your data. Now you can install PHP to process code and generate dynamic content for the web server.

While Apache embeds the PHP interpreter in each request, Nginx requires an external program to handle PHP processing and act as a bridge between the PHP interpreter itself and the web server. This allows for a better overall performance in most PHP-based websites, but it requires additional configuration. You’ll need to install php-fpm, which stands for “PHP fastCGI process manager”, and tell Nginx to pass PHP requests to this software for processing. Additionally, you’ll need php-mysql, a PHP module that allows PHP to communicate with MySQL-based databases. Core PHP packages will automatically be installed as dependencies.

To install the php-fpm and php-mysql packages, run:

```
sudo apt install php-fpm php-mysql
```

When prompted, type Y and ENTER to confirm installation. You now have your PHP components installed. Next, you’ll configure Nginx to use them.

## Configuring Nginx to Use the PHP Processor
When using the Nginx web server, we can create server blocks (similar to virtual hosts in Apache) to encapsulate configuration details and host more than one domain on a single server. In this guide, we’ll use projectLEMP as an example domain name.

Step 1: Create the root web directory for projectLEMP as follows:

```
sudo mkdir /var/www/projectLEMP
```

Step 2: Assign ownership of the directory with the $USER environment variable, which will reference your current system user:

```
sudo chown -R $USER:$USER /var/www/projectLEMP
```

Step 3: Then, open a new configuration file in Nginx’s sites-available directory using your preferred command-line editor. Here, we’ll use vim:

```
sudo vim /etc/nginx/sites-available/projectLEMP
```
This creates a blank file, paste the following bare-bones configuration:

```
server {
    listen 80;
    server_name your_domain www.your_domain;
    root /var/www/your_domain;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
```

Save and exit using :wq

<img width="506" alt="22" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/122293e6-e0f5-4932-83f8-5c59e1c5f402">

Here’s what each of these directives and location blocks do:

- listen — Defines what port Nginx will listen on. Here nginx listen on port 80, the default port for HTTP.
- root — Defines the document root where the files served by this website are stored.
- index — Defines in which order Nginx will prioritize index files for this website. It is a common practice to list index.html files with a higher precedence than index.php files to allow for quickly setting up a maintenance landing page in PHP applications. You can adjust these settings to better suit your application needs.
- server_name — Defines which domain names and/or IP addresses this server block should respond for. 
- location / — The first location block includes a try_files directive, which checks for the existence of files or directories matching a URI request. If Nginx cannot find the appropriate resource, it will return a 404 error.
- location ~ \.php$ — This location block handles the actual PHP processing by pointing Nginx to the fastcgi-php.conf configuration file and the php7.4-fpm.sock file, which declares what socket is associated with php-fpm.
- location ~ /\.ht — The last location block deals with .htaccess files, which Nginx does not process. By adding the deny all directive, if any .htaccess files happen to find their way into the document root ,they will not be served to visitors.

Step 4: Activate your configuration by linking to the config file from Nginx’s sites-enabled directory

```
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
```

Step 5: Then, unlink the default configuration file from the /sites-enabled/ directory:

```
sudo unlink /etc/nginx/sites-enabled/default
```
You can test your configuration for syntax error with this comman:

```
sudo nginx -t
```
<img width="544" alt="23" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/4b89787e-905e-48ca-8459-27534a0a1228">

If any errors are reported, go back to your configuration file to review its contents before continuing.

Step 6: When you are ready, reload Nginx to apply the changes:

```
sudo systemctl reload nginx
```
Your new website is now active, but the web root /var/www/projectLEMP is still empty. Create an index.html file in that location so that we can test that your new server block works as expected:

```
sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html 
```













