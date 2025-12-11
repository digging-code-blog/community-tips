# Eloquent Factories

## Table of Contents

- [Uncommon Methods](#uncommon-methods)
  - [`numerify`](#numerify)
  - [`lexify`](#lexify)
  - [`bothify`](#bothify)

## Uncommon Methods

### `numerify`

The `numerify` method replaces each **#** character in the given pattern with a random digit (0–9).

```php
/**
 * Define the model's default state.
 */
public function definition(): array
{
    return [
        'country_code' => $this->faker->numerify('+##'), // Example output: +20
    ];
}
```

### `lexify`

The `lexify` method replaces each **?** character with a random alphabetical character (a–z).

```php
public function definition(): array
{
    return [
        'message' => $this->faker->lexify('Hello ???'), // Example: Hello abc
    ];
}
```

### `bothify`

The `bothify` method combines the functionality of `numerify` (#) and `lexify` (?) in one pattern, allowing mixed alphanumeric placeholder generation.

```php
public function definition(): array
{
    return [
        'message' => $this->faker->bothify(
            'Hello ???, my country code is +##'
        ), // Example: Hello abc, my country code is +20
    ];
}
```
