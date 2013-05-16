Marca is using the [https://github.com/Maks3w/FR3DLdapBundle](https://github.com/Maks3w/FR3DLdapBundle) for LDAP authentication (currently v1.6)

To use the LDAP authenticate, copy the security_ldap.yml to security.yml 

The authenication will be "chained" which means that if the ldap auth fails it will roll over to the fosuserbundle for authentication.

fr3d_ldap bundle require the php ext-ldap:  sudo yum install php-ldap on RedHat

There are two additions to the parameters.yml file with this install:

    ldap_host:         xxx.xxx.xxx
    ldap_port:         xxx