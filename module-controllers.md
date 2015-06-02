# Module Controllers

- [BaseController](#base-controller)
- [BaseFrontendController](#base-frontend-controller)
- [BaseBackendController](#base-backend-controller)
- [BaseApiController](#base-api-controller)

The `Core` Module has setup 3 base controllers. Each of these controllers extends the main `BaseController` and provides some seperate functionality to prepare and render the page.

<a name="#base-controller"></a>
## <a href="#base-controller">#</a> Base Controller

This controller is what the Frontend Backend and Api Base Controllers extend, we setup some methods that we need to create a page response.

Useful methods that are inherited from this class:
- `function boot(): void`  // this method gets run when the controller has been setup
- `function setTheme($theme): bool`  // sets the current theme
- `function setLayout($layout): bool`  // sets the current layout
- `function setTitle($title, $seperator = '|'): bool`  // prepends $title to the current title (current title is set to the app name)
- `function setView($view, $data = [], $type = 'module'): object`  // determines where to load the view from
- `function getModuleNamespace($var, $module): string`  // returns a string with the module and var setup in namespace for, ready to be used in laravels views and lang functions

### setView()
This pretty much replaces the `view()` from laravel. In here, you can specify the view file, and where to load from, whether its from the `module`, `app`, `theme`, or a `custom` namespace.

```php
    return $this->setView('partials.core.login', [], 'theme');
```
This will load the login view from `/themes/<theme>/views/partials/core/login.blade.php`

```php
    return $this->setView('admin.datatable.index', [], 'module:Admin');
```
This will load the datatable view from the `admin` module doesn't matter which module you call it from. Of course the module you call to has to be installed and enabled, otherwise the namespaces wont be registered.

<a name="#base-frontend-controller"></a>
## <a href="#base-frontend-controller">#</a> BaseFrontendController

This controller is what sets up what we need for the frontend. Currently it has no added methods.
This is the controller you should extend for any frontend pages.

<a name="#base-backend-controller"></a>
## <a href="#base-backend-controller">#</a> BaseBackendController

This controller is what sets up the backend theme, and a few bits of functionality. Most the backend controllers will be extending this.

Useful methods in this class:
- `function setActions(array $actions): void`  // this sets the action buttons
- `function addPageAssets(): void`  // this method will search the assets directory to see if there is a css file for this view

<a name="#base-api-controller"></a>
## <a href="#base-api-controller">#</a> BaseApiController

The BaseApiController has a few useful methods for outputting the responses back in the needed format.

- `function sendResponse($message = 'ok', $status = 200, $data = []): void`  // sends a generic response
- `function sendError($message, $status = 500): void`  // sends an error status with message
- `function sendOK($message, $status = 200): void`  // sends and ok status with message
