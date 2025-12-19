# Eloquent Relationships

## Table of Contents

- [Touching Parent Timestamps](#touching-parent-timestamps)

---

## Touching Parent Timestamps

When a model defines a `belongsTo` or `belongsToMany` relationship to another model, such as a `Review` which belongs to a `Product`, it is sometimes helpful to update the parent's timestamp when the child model is updated.

For example, if a `Review` belongs to a `Product`, you may want the product's timestamp to reflect recent activity when reviews are added or modified.

```php
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\Relations\BelongsTo;
 
class Review extends Model
{
    /**
     * All of the relationships to be touched.
     *
     * @var array
     */
    protected $touches = ['product'];
 
    /**
     * Get the product that the review belongs to.
     */
    public function product(): BelongsTo
    {
        return $this->belongsTo(Product::class);
    }
}
```
