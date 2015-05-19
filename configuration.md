# Configuration

- [Admin Panel](#admin)
- [Module](#module)

## <a href="#admin" name="admin">#</a>Admin Panel

Once installed the system has an Administrative Panel, you can customize most of the system with these settings.
The system will save the settings into a database table `config`. Anything saved into this table can override core Laravel and Module settings alike.


## <a href="#module" name="module">#</a>Module

Each module can have it's own settings. The settings get stored in the `Config` folder under your module root. When there is an update or install, the system will automatically group the settings into the main configuration directory.

If your settings file was under the path of `./app/Modules/Blog/Config/settings.php` then when the settings get published, they will be copied to `./config/cms.blog.settings.php`. To access them from `config()` you can use the filename as the accessor string eg `config('cms.blog.settings.auto-publish')`
