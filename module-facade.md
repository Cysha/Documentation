# Module Facade

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
