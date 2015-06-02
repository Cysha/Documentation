# Module Repositories

The `Core` Module has setup a Base Eloquent Repository which you can use to extend your own Repositories and get a head start on the common functionality.

- `function getModel(): string` // simply returns the model to be used in this repository
- `function all(): Collection` // Get all the model records in the database
- `function count(): array` // Count the number of specified model records in the database
- `function create(array $data): Model` // Create a new model record in the database
- `function createMultiple(array $data): Collection` // Create one or more new model records in the database
- `function delete(): bool` // Delete one or more model records from the database
- `function deleteById($id): bool` // Delete the specified model record from the database
- `function deleteMultipleById(array $ids): int` // Delete multiple records
- `function first(): Model` // Get the first specified model record from the database
- `function get(): Collection` // Get all the specified model records in the database
- `function getById($id): Model` // Get the specified model record from the database
- `function limit($limit): $this` // Set the query limit
- `function orderBy($column, $value): $this` // Set an ORDER BY clause
- `function updateById($id, array $data): Model` // Update the specified model record in the database
- `function where($column, $value, $operator = '='): $this` // Add a simple where clause to the query
- `function whereIn($column, $value): $this` // Add a simple where in clause to the query
- `function with($relations): $this` // Set Eloquent relationships to eager load
- `function paginate($perPage = 0, $columns = ['*']): Collection` // Paginate the query
- `function transformModels($data): array` // Transforms a collection of models
