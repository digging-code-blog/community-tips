# Configuration

- [Maintenance Mode](#maintenance-mode)

## Maintenance Mode

If you’ve enabled maintenance mode and want visitors to access certain pages, you can whitelist them in your `AppServiceProvider` using the `except` method:

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
