# Cache

## Table of Contents

- [Naming Convention](#naming-convention)

## Naming Convention

This tip is not about coding per se, but about keeping your code and cache keys **cleaner and more organized**.

Instead of writing cache keys like `fooo`, it's better to use a **`namespace:resource`** pattern.

For example, if you want to cache **recent posts** and **recent comments**:

- `recent` is the **namespace**
- `posts` and `comments` are the **resources**

So, your cache keys would look like:

```php
use Illuminate\Support\Facades\Cache;

Cache::rememberForever('recent:posts', function () {
    return \App\Models\Post::latest()->take(3)->get();
});

Cache::rememberForever('recent:comments', function () {
    return \App\Models\Comment::latest()->take(5)->get();
});
```
