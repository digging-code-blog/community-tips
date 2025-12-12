# Eloquent Collections

## Table of Contents

- [Uncommon Usages](#uncommon-usages)
  - [`fresh`](#fresh)
  
## Uncommon Usages

### `fresh`

The `fresh` method allows you to **reload a model or collection from the database**, retrieving the most up-to-date data. You can also pass relationships to it, and they will be reloaded along with the model.  

```php
use App\Models\User;

$users = User::has('comments', 1)->with('comments')->get();

// Modify the first comment body locally
$users->first()->comments->first()->body = 'Updated body';

// Reload the users and their comments from the database
$users = $users->fresh('comments');
```
