well,see step to [install-xampp-on-any-linux-distro](https://luniox.blogspot.com/2023/06/how-to-install-xampp-on-any-linux-distro.html) on linux. <br>
This below step are for those who able to setup xammp on their machice.<br>
Download wordpress from <a href="https://wordpress.org/download/">link</a>
first you have you have to create file by own on your directory that install wordpress called `wp-config.php`
and paste given by wordpress

### Error on first setup

```text
To perform the requested action, WordPress needs to access your web server.
Please enter your FTP credentials to proceed. If you do not remember your credentials, you should contact your web host.
```

after searching,found this [solution](https://wordpress.org/support/topic/to-perform-the-requested-action-wordpress-needs-to-access-your-web-server-2/) <br>
**but** <br>
you have to add this

```php
define( 'FS_METHOD', 'direct');
```

on last line of `wp-config.php` <br>
Agian another

#### Installation failed: Could not create directory. /opt/lampp/htdocs/wordpress/wp-content/upgrade

to solve this you need to chanage file and folder permission `other to view and modify` simply use file manager or CLI
more detials about file permission [check this link](https://www.ubuntumint.com/linux-file-permissions/) <br>
i think all done.
