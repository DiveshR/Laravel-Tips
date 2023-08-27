# DB Models and Eloquent

# Perform operation without modifying updated_at field

```php
$user = User::first();

// `updated_at` is not changed...

User::withoutTimestamps(
     fn () => $user->update(['reserved_at' => now()])
);
```
