# Installing Vhosts

- [XAMPP/LAMP Environment](#installing_xampp)

<a name="installing_xampp"></a>
### <a href="#installing_xampp">#</a> XAMPP/LAMP Environment

After running the above commands, a [vhost](http://httpd.apache.org/docs/2.2/vhosts/) needs to be set up. This is how you do it in [xampp](https://www.apachefriends.org/index.html) for linux:
**Note:** tested with Apache/2.4.12 (Unix)

1. Set up your `/etc/hosts` by adding a new entry. This is what you'll use to access the CMS. It would be a wise idea to refer to your distribution's guide on how to do this.
Example given:

```
# Custom vhosts
127.0.0.1    pxcms.localdomain
```

2. Open `/opt/lampp/etc/httpd.conf` with your favorite editor and uncomment the inclusion of the `/opt/lampp/etc/httpd.conf` file.
3. Modify `/opt/lampp/etc/extra/httpd-vhosts.conf` to suite your needs. `DocumentRoot` **should** point to `/public`. Here's an example:

```apacheconf
<VirtualHost *:80>
    DocumentRoot "/opt/lampp/htdocs/pxcms/public"
    ServerName pxcms.localdomain
    ServerAlias www.pxcms.localdomain.com
    ErrorLog "logs/pxcms-error_log"
    CustomLog "logs/pxcms-access_log" common
</VirtualHost>
```

In this case, the CMS is installed in the `pxcms` directory under the htdocs root. `pxcms.localdomain` is used to access the CMS. Logs are stored in the `logs/` directory under lampp root.
