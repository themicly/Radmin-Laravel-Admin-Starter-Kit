## Upgrade to Laravel 9 Guide
#### Requirements
Required PHP version is `"php": "^8.0"`

#### Dependencies
Please update the following dependencies in your application's `composer.json` file:
1. `laravel/framework` to `^9.0`
2. `fruitcake/laravel-cors` to `^3.0`
3. `spatie/laravel-permission` to `^5.0`
4. `nunomaduro/collision` to `^6.0`

In addition,  please replace `"facade/ignition": "^2.3.6"` with `"spatie/laravel-ignition": "^1.0"`. and remove `fideloper/proxy`.

#### Trusted Proxies
Please update your application's `trusted proxy` middleware.
Within your `app/Http/Middleware/TrustProxies.php` file, update use `Fideloper\Proxy\TrustProxies as Middleware` to use `Illuminate\Http\Middleware\TrustProxies as Middleware`.

Next, within `app/Http/Middleware/TrustProxies.php`, you should update the $headers property definition:

```php
// Before...
protected $headers = Request::HEADER_X_FORWARDED_ALL;
 
// After...
protected $headers =
    Request::HEADER_X_FORWARDED_FOR |
    Request::HEADER_X_FORWARDED_HOST |
    Request::HEADER_X_FORWARDED_PORT |
    Request::HEADER_X_FORWARDED_PROTO |
    Request::HEADER_X_FORWARDED_AWS_ELB;
```

And finally Run `composer install`

If you faced any issue please go through this upgrade guideline https://laravel.com/docs/9.x/upgrade#updating-dependencies
