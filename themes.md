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


