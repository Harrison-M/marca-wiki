Marca is using the [https://github.com/Maks3w/FR3DLdapBundle](https://github.com/Maks3w/FR3DLdapBundle) for LDAP authentication (currently v1.6)

To use the LDAP authenticate, copy the security_ldap.yml to security.yml 

The authenication will be "chained" which means that if the ldap auth fails it will roll over to the fosuserbundle for authentication.

fr3d_ldap bundle require the php ext-ldap:
 
(on RedHat) 

    sudo yum install php-ldap

(on Ubuntu/Debian)

    sudo apt-get install php5-ldap

There are three additions to the parameters.yml file with this install:

    ldap:              Yes/No
    ldap_host:         xxx.xxx.xxx
    ldap_port:         xxx

Set Ldap to yes to turn on Ldap authentication on your install, and to no to turn it off. If you aren't using Ldap, set host and port to xxxx, as shown. Blank values will throw an error.  