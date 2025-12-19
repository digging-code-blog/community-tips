# Eloquent

## Table of Contents

- [Default Attributes Values](#default-attributes-values)

---

## Default Attributes Values

In Eloquent, you can set default values for model attributes when a model is instantiated using the `$attributes` property.

```php
use Illuminate\Database\Eloquent\Model;

class Item extends Model
{
    /**
     * The model's default values for attributes.
     *
     * @var array
     */
    protected $attributes = [
        'title'   => 'New Item', // Default title for new items
        'options' => '[]',
    ];
}
```

>[!NOTE]
> Values assigned in the `$attributes` array should be in their raw, "storable" format—just as they would appear if retrieved directly from the database.
