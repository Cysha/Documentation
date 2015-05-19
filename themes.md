# Themes

- [Structure](#structure)
- [Basics](#basics)
- [Managing Themes](#managing-themes)

<a name="structure"></a>
## <a href="#structure">#</a> Structure

`PXCMS` uses [`teepluss/laravel-theme`](https://github.com/teepluss/laravel-theme) for theme support.

A theme has the following structure.
```
themes/
  ├── Default/
    ├── assets/
    ├── layouts/
        ├── 1-column.blade.php
        ├── 2-column-left.blade.php
        ├── 2-column-right.blade.php
        ├── 3-column.blade.php
        ├── basic.blade.php
        ├── default.blade.php
        ├── homepage.blade.php
        ├── single.blade.php
    ├── resources/
        ├── assets/
            ├── js/
            ├── less/
    ├── views/
        ├── home/
        ├── partials/
            ├── core/
            ├── theme/
    ├── bower.json
    ├── composer.json
    ├── config.php
    ├── gulpfile.json
    ├── package.json
    ├── theme.json
```

<a name="basics"></a>
## <a href="#basics">#</a> Basics

Each theme has a few default files to allow certain things to happen.
- `config.php` will be used by the theme package to allow you to set some sane defaults.
- `theme.json` is the file the CMS will use to identify the theme.
- `package.json` `gulpfile.json` and `bower.json` are all used by NPM, Gulp and Bower to manage the themes dependencies. These dependencies are things like Bootstrap, Font Awesome, jQuery etc.

<a name="managing-themes"></a>
## <a href="#managing-themes">#</a> Managing Themes

Themes can be managed via the Admin Panel. If your user has the correct permissions, there will be a link on the left sidebar titled `Theme Manager`. This will enable you to switch the default frontend & backend themes.

At this time, there are no configuration options available for themes.

