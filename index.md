# Getting Started

- [System Requirements](#sysrequirements)
- [Installing](#installing)
- [Scheduler](#scheduler)

PhoenixCMS(`PXCMS`) is built on top of `Laravel 5` this provides us with a nice stable base from which to build on top of.

<a name="sysrequirements"></a>
## <a href="#sysrequirements">#</a> System Requirements

`PXCMS` needs the following to run correctly, missing any of these will result in missing or broken functionality, or might even make the system not work at all.

- Composer
- PHP 5.4 or higher
- Mcrypt PHP Extension
- OpenSSL PHP Extension
- Mbstring PHP Extension
- Tokenizer PHP Extension

Laravel states that
> As of PHP 5.5, some OS distributions may require you to manually install the PHP JSON extension. When using Ubuntu, this can be done via `apt-get install php5-json`.

*Development Requirements*
- Local Git Client
- NPM
- Bower

<a name="installing"></a>
## <a href="#installing">#</a> Installing

To install `PXCMS` first clone the main project.
> `git clone https://github.com/Cysha/PhoenixCMS.git .`

This will get you a copy of the main project without any themes or modules. At this point you can customize the `composer.json` as you see fit, add some more modules, or some alternate themes.

Once you are happy, you can run `composer install`, this will run a full system install, grabbing everything it needs to run. **This can take a few minutes**. While that is going, you will need to duplicate `.env.example` to `.env` this will contain the core configuration details, make sure the details are correct in there.

Next step will be to run `php artisan cms:install` from the projects root directory. If the installer cannot make a connection to the database you will see an error message and will need to fix it before continuing.

The Installer will ask you if you want to install the database and then again if you want to seed the data. Say `yes` to both of these questions.

Unless you ran into problems, Your instance should be installed and ready to go.

### <a href="#installing_xampp">#</a> Installing in a xampp/lampp environment

After running the above commands, a [vhost](http://httpd.apache.org/docs/2.2/vhosts/) needs to be set up. This is how you do it in [xampp](https://www.apachefriends.org/index.html) for linux:  
**Note:** tested with Apache/2.4.12 (Unix)

1. Set up your `/etc/hosts` by adding a new entry. This is what you'll use to access the CMS. It would be a wise idea to refer to your distribution's guide on how to do this.  
Example given:

>```
># Custom vhosts
>127.0.0.1    pxcms.localdomainpxcms    storm
>```

2. Open `/opt/lampp/etc/httpd.conf` with your favorite editor and uncomment the inclusion of the `/opt/lampp/etc/httpd.conf` file.
3. Modify `/opt/lampp/etc/extra/httpd-vhosts.conf` to suite your needs. `DocumentRoot` **should** point to `/public`. Here's an example:

>```
><VirtualHost *:80>
>    DocumentRoot "/opt/lampp/htdocs/pxcms/public"
>    ServerName pxcms.localdomain
>    ServerAlias www.pxcms.localdomain.com
>    ErrorLog "logs/pxcms-error_log"
>    CustomLog "logs/pxcms-access_log" common
></VirtualHost>
>```

In this case, the CMS is installed in the `pxcms` directory under the htdocs root. `pxcms.localdomain` is used to access the CMS. Logs are stored in the `logs/` directory under lampp root.

<a name="scheduler"></a>
## <a href="#scheduler">#</a> Cron Scheduler

Here is the only Cron entry you need to add to your server:

> `* * * * * php /path/to/artisan schedule:run 1>> /dev/null 2>&1`

This Cron will call the Laravel command scheduler every minute. This will run any commands that are due to run from the installed modules.
