# Configuration

## Table of Contents

- [Maintenance Mode](#maintenance-mode)

## Maintenance Mode

If you've enabled maintenance mode in Laravel 11+ and want visitors to access specific pages, you can whitelist them in your `AppServiceProvider` using the `except` method:

```php
use Illuminate\Foundation\Http\Middleware\PreventRequestsDuringMaintenance;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     */
    public function boot(): void
    {
        PreventRequestsDuringMaintenance::except([
            '/register',
            '/register/*',
            '/terms',
            '/privacy',
        ]);
    }
}
```
