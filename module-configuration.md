# Module Configuration

- [Introduction](#introduction)
- [Modules Config Directory](#config-directory)
    - [menus.php](#menusphp)
    - [permissions.php](#permissionsphp)
    - [widgets.php](#widgetsphp)

<a name="introduction"></a>
## <a href="#introduction">#</a> Introduction

The modules have a few different config files that the system will use.
This page will give you an overview of the base config files.

<a name="config-directory"></a>
## <a href="#config-directory">#</a> Modules Config Directory

Each file gets stored in the `Config` folder under your module root.
Changes to the modules config files wont be immediately realized by the system, to get around this, you can run

> `php artisan modules:publish-config --force`

in the command line and it will make the system update the config files and clear the cache.

<a name="menusphp"></a>
### <a href="#menusphp">#</a> menus.php

```php
<?php

return [

    'backend_sidebar' => [
        [
            'route' => 'pxcms.admin.index',
            'text' => 'Dashboard',
            'icon' => 'fa-dashboard',
            'order' => 1,
        ],
        'User Management' => [],
        'System' => [
            [
                'route' => 'admin.config.website',
                'text' => 'Configuration',
                'icon' => 'fa-wrench',
                'order' => 1,
                'permission' => 'manage@admin_config',
                'activePattern' => '\/{backend}\/config\/*',
            ],
            [
                'route' => 'admin.config.theme',
                'text' => 'Theme Manager',
                'icon' => 'fa-image',
                'order' => 2,
                'permission' => 'theme@admin_config'
            ],
        ],
    ],

];
```

This example builds the Sidebar in the admin panel. As you can see it is quite simple to build, only requiring a few keys in each array element.

The root key is the menu name, you can use this to render the menu in a view with the following blade helper: `@menu('backend_sidebar')`.

Once in side the root array, you can immedately add menu items as is the case with the `Dashboard` link, or you can setup sub menus, as is done with the `System`, In this case as `User Management` has nothing in, it will not be rendered.

Each link array element has a set of keys that can be used to build the link up. Most of these can be set to null or removed without issue.

- `route` // this is the route name
- `url` // if you don't have a route for this link, you can specify a url directly
- `text` // the text to render on the link
- `icon` // a font awesome icon to add before the text
- `order` // the position for this link(other modules might add links in that throw this out)
- `permission` // if the route requires a permission, add it here, if the user doesn't have permission, the link won't show
- `activePattern` // a regex pattern to match against the url, if this matches, an active class is added to the link.

> `activePattern` will also replace `{backend}` `{frontend}` and `{api}` with their paths from the configuration page for easier resolving.

<a name="permissionsphp"></a>
### <a href="#permissionsphp">#</a> permissions.php

Permissions are very simple to add to the system. Each permission is basically `permission` => `readable_name`, these are stored by a resource.

```php
<?php

return [
    'auth_user' => [
        'manage' => 'Manage users',
        'manage.create' => 'Create a user',
        'manage.read' => 'Read a user',
        'manage.update' => 'Update a user',
        'manage.delete' => 'Delete a user',
    ],
];
```

Using the example code above, the resource is `auth_user` this is made up of the module name, and the model name, this gives us a standard which should avoid any clashes with other modules.

Using the menus and middleware `hasPermission`, you can define permissions to check for. These are formatted `permission`@`resource`.

To check if the user has permission to manage the users
```php
Lock::can('manage', 'auth_user');
```

This will return a bool value based on how the permissions have been decided. By default any permissons that have not been decided will be `false`.


<a name="widgetsphp"></a>
### <a href="#widgetsphp">#</a> widgets.php

The CMS has support for widgets, to register these, you need to have a widgets.php configuration file in your module. That config file looks like this:

```php
<?php

return [
    'dashboard' => [
        [
            'view'  => 'admin::widgets.cmsUpdate',
            'name'  => 'CMS Update Info',
            'class' => '\Cms\Modules\Admin\Composers\Widgets@CmsUpdate',
        ],
    ],
];
```

Currently only the Backend Dashboard supports using the widgets, luckily registering these are very simple.

Each array element has 3 keys:
- `view` // the namespaced path to the view
- `name` // a readable name for this widget
- `class` // a fully namespaced `class`@`method` string for the composer

When registering a widget, the system will also register the composer onto the view so you have the needed data.
