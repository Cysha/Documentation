# Modules

- [Structure](#structure)
- [Module Entity](#module-entity)
- [Commands](#commands)

<a name="structure"></a>
## <a href="#structure">#</a> Structure
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
<a name="module-entity"></a>
## <a href="#module-entity">#</a> Module Entity
You can gather information from a module by using the `Module::find()`

From there you can do a range of things:
- `$module->getName()` // Gets the module name
- `$module->getLowerName()` // Gets the module name in lowercase
- `$module->getStudlyName()` // Gets the module name in Studly case
- `$module->getPath()` // Gets the module's install path
- `$module->getExtraPath()` // Gets a path to a file or folder in a module
- `$module->enable()` // Enable the module
- `$module->disable()` // Disable the module
- `$module->delete()` // Delete a module

<a name="commands"></a>
## <a href="#commands">#</a> Commands

<table class="table table-striped table-bordered">
    <thead>
        <tr>
            <th>Command</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th colspan="2">Base Commands</th>
        </tr>
        <tr>
            <td>module:dump</td>
            <td>Dump-autoload the specified module or for all module.</td>
        </tr>
        <tr>
            <td>module:enable</td>
            <td>Enable the specified module.</td>
        </tr>
        <tr>
            <td>module:disable</td>
            <td>Disable the specified module.</td>
        </tr>
        <tr>
            <td>module:install</td>
            <td>Install the specified module by given package name (vendor/name).</td>
        </tr>
        <tr>
            <td>module:update</td>
            <td>Update dependencies for the specified module or for all modules.</td>
        </tr>
        <tr>
            <td>module:list</td>
            <td>Show list of all modules.</td>
        </tr>
        <tr>
            <td>module:seed</td>
            <td>Run database seeder from the specified module or from all modules.</td>
        </tr>
        <tr>
            <td>module:setup</td>
            <td>Setting up modules folders for first use.</td>
        </tr>
        <tr>
            <td>module:use</td>
            <td>Use the specified module.</td>
        </tr>
        <tr>
            <th colspan="2">Make Commands</th>
        </tr>
        <tr>
            <td>module:make</td>
            <td>Generate new module.</td>
        </tr>
        <tr>
            <td>module:make-command</td>
            <td>Generate new Artisan command for the specified module.</td>
        </tr>
        <tr>
            <td>module:make-controller</td>
            <td>Generate new restful controller for the specified module.</td>
        </tr>
        <tr>
            <td>module:make-middleware</td>
            <td>Generate new filter for the specified module.</td>
        </tr>
        <tr>
            <td>module:make-migration</td>
            <td>Generate a new migration for the specified module.</td>
        </tr>
        <tr>
            <td>module:make-model</td>
            <td>Generate new model for the specified module.</td>
        </tr>
        <tr>
            <td>module:make-provider</td>
            <td>Generate a new service provider for the specified module.</td>
        </tr>
        <tr>
            <td>module:make-request</td>
            <td>Generate new form request class for the specified module.</td>
        </tr>
        <tr>
            <td>module:make-seed</td>
            <td>Generate new seeder for the specified module.</td>
        </tr>
        <tr>
            <th colspan="2">Migration Commands</th>
        </tr>
        <tr>
            <td>module:migrate</td>
            <td>Migrate the migrations from the specified module or from all modules.</td>
        </tr>
        <tr>
            <td>module:migrate-refresh</td>
            <td>Rollback & re-migrate the modules migrations.</td>
        </tr>
        <tr>
            <td>module:migrate-reset</td>
            <td>Reset the modules migrations.</td>
        </tr>
        <tr>
            <td>module:migrate-rollback</td>
            <td>Rollback the modules migrations.</td>
        </tr>
        <tr>
            <th colspan="2">Publish Commands</th>
        </tr>
        <tr>
            <td>module:publish</td>
            <td>Publish assets from the specified module or from all modules.</td>
        </tr>
        <tr>
            <td>module:publish-config</td>
            <td>Publish a modules configuration</td>
        </tr>
        <tr>
            <td>module:publish-migration</td>
            <td>Publish a module's migrations to the application</td>
        </tr>
        <tr>
            <td>module:route-provider</td>
            <td>Generate a new route service provider for the specified module.</td>
        </tr>
    </tbody>
</table>

