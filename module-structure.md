# Module Structure

`PXCMS` uses [`ping-pong/modules`](http://sky.pingpong-labs.com/docs/2.0/modules) for modular support.

A module has the following structure.
```
app/
  ├── Modules/
    ├── Blog/
      ├── Config/
      ├── Console/
      ├── Database/
         ├── Migrations/
         ├── Seeders/
      ├── Models/
      ├── Http/
        ├── Controllers/
        ├── Middleware/
        ├── Requests/
        ├── routes-api.php
        ├── routes-frontend.php
        ├── routes-backend.php
      ├── Providers/
        ├── BlogModuleServiceProvider.php
      ├── Resources/
        ├── assets/
        ├── lang/
        ├── views/
      ├── Repositories/
      ├── Tests/
      ├── Traits/
      ├── composer.json
      ├── module.json
      ├── start.php
```
