# Eloquent Serialization

## Table of Contents

- [Uncommon Usages](#uncommon-usages)
  - [Attribute Visibility](#attribute-visibility)
    - [`visible` / `hidden`](#visible--hidden)
    - [`makeVisible` / `makeHidden`](#makevisible--makehidden)
    - [`mergeVisible` / `mergeHidden`](#mergevisible--mergehidden)
  
## Uncommon Usages

### Attribute Visibility

Laravel provides attributes to control the visibility of model properties when converting models to arrays or JSON. You may already know about the `visible` and `hidden` properties, but **you can also include relationship names** to control their visibility during retrieval.

#### `visible` / `hidden`

```php
use Illuminate\Foundation\Auth\User as Authenticatable;

class User extends Authenticatable
{
    /**
     * The attributes that should be visible in arrays.
     *
     * @var array
     */
    protected $visible = [
        'name',
        'email',
        'created_at',
        'comments', // one-to-many relationship
    ];
}
```

The same logic applies to the hidden attribute. You can hide both model attributes and relationships when serializing your models.

#### `makeVisible` / `makeHidden`

You can override visibility attributes at runtime using `makeVisible` and `makeHidden`:

```php
$users = \App\Models\User::withWhereHas('comments')->get();

$users->makeVisible(['updated_at']);
// $users->makeHidden(['created_at', 'updated_at']);

return $users;
```

> [!NOTE]
> These methods work with single model instances as well as collections.

#### `mergeVisible` / `mergeHidden`

You can also control these attributes at runtime using the `mergeVisible` and `mergeHidden` methods. This is useful when you want to temporarily adjust visibility for a specific model instance.

```php
$user = \App\Models\User::withWhereHas('comments')->first();

$user->mergeVisible(['created_at']);

return $user;
```

> [!NOTE]
> These methods work only with single model instances, not collections.
