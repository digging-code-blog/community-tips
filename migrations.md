# Migrations

## Table of Contents

- [Uncommon Methods](#uncommon-methods)
  - [`invisible`](#invisible)
  - [`temporary`](#temporary)
  - [`from`](#from)

## Uncommon Methods

### `invisible`

The `invisible` column modifier hides a column from default `SELECT` queries.
It still exists in the table, but it will not appear unless explicitly requested in the query.

```php
use Illuminate\Support\Facades\Schema;
use Illuminate\Database\Schema\Blueprint;

Schema::create('users', function (Blueprint $table) {
    $table->timestamp('email_verified_at')
          ->nullable()
          ->invisible();
});
```

### `temporary`

The `temporary` method creates a temporary table that exists only for the duration of the current database session.
Once the connection is closed, the table is automatically dropped.

```php
use Illuminate\Support\Facades\Schema;
use Illuminate\Database\Schema\Blueprint;

Schema::create('users', function (Blueprint $table) {
    $table->temporary();
});
```

### `from`

The `from` method defines the starting value for an auto-incrementing column.

```php
use Illuminate\Support\Facades\Schema;
use Illuminate\Database\Schema\Blueprint;

Schema::create('users', function (Blueprint $table) {
    $table->integer('age')->from(16);
});
```
