# DB Models and Eloquent

# Perform operation without modifying updated_at field

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
