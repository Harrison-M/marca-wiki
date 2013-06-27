The following are notes about how to get Ubuntu and an development installation of Marca up and running on a Mac.


**Install VirtualBox / Install rEFIt and Partition HD**

To set up a dual boot configuration, follow [these instructions]
(https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation).

In essence, you'll perform the following:
* Back up your data
* Install [rEFIt] (http://refit.sourceforge.net/doc/c1s1_install.html)
* Partition your drive using Disk Utility (we tried the Boot Camp instructions, but found Disk Utility to be simpler)
* Burn the [Ubuntu ISO](https://help.ubuntu.com/community/BurningIsoHowto) to either a CD or a flash drive (we found the flash drive to be easier / faster)
* Follow the Ubuntu install instructions

Alternately, you can install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and install an Ubuntu ISO.

If you create an Ubuntu virtual machine using VirtualBox, be sure to change the following settings from defaults (most advice adapted from [here](http://www.howtogeek.com/124796/the-htg-guide-to-speeding-up-your-virtual-machines/):
* Base memory as high as your system will allow (2GB recommended)
* As many processors as you can spare (4 recommended)
* Video memory as high as allowed (128MB recommended)
* Install guest additions (see linked article)
* Used a fixed size virtual disk, unless you're tight on space / running a SSD
* Don't enable 3D acceleration (makes the mouse behave oddly)


**Install Apache**

Once you've installed Ubuntu, open the Terminal, and run the following commands to install Apache
``sudo apt-get install apache2``  
``sudo service apache2 start``


**Install MySQL**

Next, install and configure MySQL (again, from the Terminal):
``sudo apt-get install mysql-server``

Run the following to open MySQL:
``mysql -u root -p``

(Note: substitute your username for ``john`` throughout this guide)

``CREATE USER 'john'@'localhost' IDENTIFIED BY 'mypass';``  
``GRANT ALL PRIVILEGES ON *.* TO 'john'@'localhost' WITH GRANT OPTION;``


**Install PHP**

Run the following commands from the Terminal to install PHP:
``sudo apt-get install php5-cli``  
``sudo apt-get install libapache2-mod-php5``  
``sudo apt-get install php5-ldap``  
``sudo apt-get install php5-mysql``  
``sudo service apache2 restart``  

Next, you'll need to edit your php.ini file. From the terminal, run the following to open php.ini in a text editor:

``sudo gedit /etc/php5/cli/php.ini``  
Within gedit, search for ``;date.timezone``

Delete the semicolon and set the value to "America/New_York" (or your timezone) so that the line of code looks like this:

``date.timezone = America/New_York``

Save the file. Then, on the Terminal, run:

``sudo service apache2 restart``


**Install Git**

In the Terminal, run:

``sudo apt-get install git``


**Install Curl**

In the Terminal, run:

``sudo apt-get install curl libcurl3 libcurl3-dev php5-curl``  


**Install Composer**

In the Terminal, first log in as superuser (not strictly necessary, but helps overcome occasional problems with running commands with ``sudo``):

``sudo su -``

Then, run the following:

``cd /var/www``  
``sudo curl -sS https://getcomposer.org/installer | php``  
``exit``  


**Install Marca**

Hooray! This is the whole point of this exercise, right?

In the terminal, run:

``git clone https://github.com/calliopeinitiative/marca.git``  
``sudo chown -R john:john marca``  
``sudo curl -sS https://getcomposer.org/installer | php``  
``sudo php composer.phar update``  

(Note: don't worry about any error messages Composer throws at this point)


**Install JDK and NetBeans with PHP**

We use NetBeans as our IDE. If you feel like using something else, go for it.

In the Terminal, run:

``sudo apt-get install openjdk-6-jdk``

Then, in a web browser, go [here](https://netbeans.org/downloads/start.html?platform=linux&lang=en&option=php) to download NetBeans with PHP.

Once the file's downloaded, in the Terminal, run:

``cd /Home/john/Downloads``  
``sudo chmod +x netbeans-7.3.1-php-linux.sh``  
``./netbeans-7.3.1-php-linux.sh``  

(Note: the first open of the software will be extremely slow. Also, for some reason, I had to open NetBeans multiple times / restart Ubuntu to get NetBeans to open successfully for the first time. YMMV)


**Configuring Marca**

Once NetBeans is open, perform the following (leaving everything else as default):
* Create new PHP projects from existing files in /var/www/marca
* Set index file to web/app_dev.php

Also, you'll need to install the TWIG extensions (waiting on notes from Ron for this)

Once you've opened Marca in NetBeans, take the following steps:
* In ``app/config``, copy parameters.yml.dist as parameters.yml
* Run ``sudo php composer.phar update`` in the Terminal
* Back in NetBeans, still in ``app/config``, copy security_fos_only.yml as security.yml

Next, fill in parameters.yml with the following information:
``parameters:
    database_driver:   pdo_mysql
    database_host:     localhost
    database_port:     null
    database_name:     marca_db
    database_user:     john
    database_password: nahtan0j

    mailer_transport:  smtp
    mailer_host:      localhost
    mailer_port:       25
    mailer_sender_address: john@gomarca.com
    mailer_user:       john
    mailer_password:   nahtan0j
    mailer_encryption:  tls
    from_email:        john@gomarca.com

    wkhtmltopdf_path:  /usr/local/bin/wkhtmltopdf-i386
    ldap_host:         xxx.xxx.xxx
    ldap_port:         xxx

    locale:            en
    secret:            agr8hqoiugq34iqn34g8q0348gq7435
    app_name:          Marca
    ldap:              no

    upload_path:       %kernel.root_dir%/../uploads/files``

Next, run the following in the Terminal:
``sudo php composer.phar update``  
``app/console doctrine:database:create``  
``app/console doctrine:schema:update --force``  
``sudo chmod -R 777 app/cache app/logs``  

Next, install fixtures:

``app/console doctrine:fixtures:load``

(If you run into trouble here, you may need to delete the file ``/var/www/marca/src/Marca/DocBundle/DataFixtures/ORM/AdditionalFixtures/UGAMarkupSet.php``)

Finally, since our fixtures are out of date, open MySQL:

``mysql -u john -p``

and run the following:

``use marca_db``  
``insert into institution (name,payment_type,semester_price) values ('University of Georgia','0','0');``  
``sudo chmod -R 777 app/cache app/logs``  

You can now login with the following:

* Username: testinstructor1
* Password: test1

If you'd like to set yourself up as an admin, in the Terminal, type:

``sudo app/console fos:user:promote testinstructor1 ROLE_ADMIN``

And you should be (mostly) good to go! More updates to come (hopefully).