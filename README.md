# Laravel Trashmail Rules

[![Latest Version](http://img.shields.io/packagist/v/elbgoods/laravel-trashmail-rule.svg?label=Release&style=for-the-badge)](https://packagist.org/packages/elbgoods/laravel-trashmail-rule)
[![MIT License](https://img.shields.io/github/license/elbgoods/laravel-trashmail-rule.svg?label=License&color=blue&style=for-the-badge)](https://github.com/elbgoods/laravel-trashmail-rule/blob/master/LICENSE)
[![Offset Earth](https://img.shields.io/badge/Treeware-%F0%9F%8C%B3-green?style=for-the-badge&cacheSeconds=600)](https://offset.earth/treeware)

[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/elbgoods/laravel-trashmail-rule/run-tests?label=tests&style=flat-square)](https://github.com/elbgoods/laravel-trashmail-rule/actions?query=workflow%3Arun-tests)
[![Total Downloads](https://img.shields.io/packagist/dt/elbgoods/laravel-trashmail-rule.svg?style=flat-square)](https://packagist.org/packages/elbgoods/laravel-trashmail-rule)

This package provides a validation rule to prevent trashmail email addresses.

## Installation

At first you have to add this package to your `composer.json`:

```bash
composer require elbgoods/laravel-trashmail-rule
```

After this you can publish the package translation files to adjust the error messages:

```bash
php artisan vendor:publish --provider="Elbgoods\TrashmailRule\TrashmailRuleServiceProvider" --tag=lang
php artisan vendor:publish --provider="Elbgoods\TrashmailRule\TrashmailRuleServiceProvider" --tag=config
```

## Configuration

The package provides a configuration to define the rule behaviour.

### Dead-Letter.Email

By default the package uses an up-to-date blacklist by [Dead-Letter.Email](https://www.dead-letter.email/). 
You can disable this in the config and control the caching behaviour.

### Blacklist

You can add your own blacklist, these domains will always be blocked - independent if they are part of Dead-Letter.Email or not.

### Whitelist

If you want to pass some domains always you can add them to the whitelist. These domains will always pass, even if they are listed in the blacklist.

## Usage

This package provides a basic `TrashmailRule` which you can use. All more specific rules only extend this rule with a predefined `format`.

```php
use Elbgoods\TrashmailRule\Rules\TrashmailRule;

$rule = new TrashmailRule();
```

By default the rule requires a value - if you want to accept `null` values you can use the `nullable()` method or set the `$required` parameter to `false`.

```php
use Elbgoods\TrashmailRule\Rules\TrashmailRule;

$rule = new TrashmailRule(false);
$rule->nullable();
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Versioning

This package follows [semantic versioning](https://semver.org/).

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

Please see [SECURITY](SECURITY.md) for details.

## Credits

- [Tom Witkowski](https://github.com/Gummibeer)
- [All Contributors](https://github.com/elbgoods/laravel-trashmail-rule/graphs/contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.

## Treeware

You're free to use this package, but if it makes it to your production environment we would highly appreciate you buying or planting the world a tree.

It’s now common knowledge that one of the best tools to tackle the climate crisis and keep our temperatures from rising above 1.5C is to [plant trees](https://www.bbc.co.uk/news/science-environment-48870920). If you contribute to my forest you’ll be creating employment for local families and restoring wildlife habitats.

You can buy trees at https://offset.earth/treeware

Read more about Treeware at https://treeware.earth

[![We offset our carbon footprint via Offset Earth](https://toolkit.offset.earth/carbonpositiveworkforce/badge/5e186e68516eb60018c5172b?black=true&landscape=true)](https://offset.earth/treeware)
