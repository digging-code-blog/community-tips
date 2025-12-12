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

You can temporarily modify a model's visibility attributes using `makeVisible` and `makeHidden` methods.

```php
use App\Models\User;

$users = User::withWhereHas('comments')->get();

$users->makeVisible(['updated_at']);
// $users->makeHidden(['created_at', 'updated_at']);

return $users;
```

> [!NOTE]
> These methods work with single model instances as well as collections.

#### `mergeVisible` / `mergeHidden`

The `mergeVisible` and `mergeHidden` methods allow you to dynamically control the visibility of attributes at runtime.

```php
use App\Models\User;

$user = User::first();

$user->mergeVisible(['updated_at']);
// $user->mergeHidden(['profile_views']);

return $user;
```

> [!NOTE]
> These methods work only with single model instances, not collections.
