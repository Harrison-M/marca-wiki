Marca is using the [https://github.com/Maks3w/FR3DLdapBundle](https://github.com/Maks3w/FR3DLdapBundle) for LDAP authentication (currently v1.6)

To use the LDAP authenticate, copy the security_ldap.yml to security.yml 

The authenication will be "chained" which means that if the ldap auth fails it will roll over to the fosuserbundle for authentication.

fr3d_ldap bundle require the php ext-ldap:
 
(on RedHat) 

    sudo yum install php-ldap

There are two additions to the parameters.yml file with this install:

    ldap_host:         xxx.xxx.xxx
    ldap_port:         xxx

There is also a twig global named ldap_auth (yes|no) that will hide the the Forgot Password? and the Change Password.