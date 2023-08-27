# DB Models and Eloquent

## Perform operation without modifying updated_at field

```php
$user = User::first();

// `updated_at` is not changed...

User::withoutTimestamps(
     fn () => $user->update(['reserved_at' => now()])
);
```

# Eloquent where date methods

```php
$users = User::whereDate('created_at', '2023-08-27')->get();
$users = User::whereMonth('created_at', '8')->get();
$users = User::whereDay('created_at', '2')->get();
$users = User::whereYear('created_at', date('Y'))->get();
$users = User::whereTime('created_at', '=', '20:32:11')->get();
```

# Model all: columns  
When calling Eloquent's Model::all(), you can specify which columns to return.

```php
$users = User::all(['id', 'name', 'email']);
```

# Change Default Timestamp Fields
When calling Eloquent's Model::all(), you can specify which columns to return.

```php
class User extends Model
{
    const CREATED_AT = 'create_time';
    const UPDATED_AT = 'update_time';
}
```

# Order by created_at
Instead of:


```php
User::orderBy('created_at', 'desc')->get();
```
Shorter Code:
```php
User::latest()->get();
```
NOTE: By default, latest() will order by created_at.
