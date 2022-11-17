# multisite-wordpress

## Configuración

Modificar el archivo `wp-config.php`

```php
// Activate multi site support
define( 'MULTISITE', true );

// If new blogs should be created as subdomain
define( 'SUBDOMAIN_INSTALL', false ); 
$base = '/';

// Domain name for WP Multi-Site
define('DOMAIN_CURRENT_SITE', '');
```

## Documentación

- [https://www.hostinger.mx/tutoriales/todo-lo-que-necesitas-saber-para-activar-y-utilizar-wordpress-multisite][1]
- [https://www.hostinger.com/tutorials/activate-wordpress-multisite][2]
- [https://wetopi.com/es/wordpress-multisite-con-subdirectorios/][3]
- [https://www.a2hosting.com/kb/installable-applications/optimization-and-configuration/wordpress2/configuring-a-wordpress-multisite-network][4]
- [https://www.cloudways.com/blog/use-react-with-wordpress-to-create-headless-cms/][5]
- [https://ayudawp.com/headless-wordpress-cms/][6]
- [https://kinsta.com/es/blog/multisitio-wordpress/][7]
- https://docs.bitnami.com/ibm/apps/wordpress-multisite/configuration/configure-wordpress-multisite/
- https://gist.github.com/thomasarie/4140384
- https://www.youtube.com/watch?v=QvEmidLrYjo

Documentación oficial de Wordpress:

- [https://wordpress.org/support/article/installing-multiple-blogs/][8]
- [https://wordpress.org/support/article/wordpress-multisite-domain-mapping/][9]
- [https://wordpress.org/support/article/moving-wordpress/#moving-wordpress-multisite][10]
- [https://wordpress.org/support/article/multisite-network-administration/][11]

[1]:	https://www.hostinger.mx/tutoriales/todo-lo-que-necesitas-saber-para-activar-y-utilizar-wordpress-multisite
[2]:	https://www.hostinger.com/tutorials/activate-wordpress-multisite
[3]:	https://wetopi.com/es/wordpress-multisite-con-subdirectorios/
[4]:	https://www.a2hosting.com/kb/installable-applications/optimization-and-configuration/wordpress2/configuring-a-wordpress-multisite-network
[5]:	https://www.cloudways.com/blog/use-react-with-wordpress-to-create-headless-cms/
[6]:	https://ayudawp.com/headless-wordpress-cms/
[7]:	https://kinsta.com/es/blog/multisitio-wordpress/
[8]:	https://wordpress.org/support/article/installing-multiple-blogs/
[9]:	https://wordpress.org/support/article/wordpress-multisite-domain-mapping/
[10]:	https://wordpress.org/support/article/moving-wordpress/#moving-wordpress-multisite
[11]:	https://wordpress.org/support/article/multisite-network-administration/