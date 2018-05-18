<p align="center"><img src="https://laravel.com/assets/img/components/logo-cashier.svg"></p>

## Introduction

Laravel Cashier provides an expressive, fluent interface to [Stripe's](https://stripe.com) subscription billing services. It handles almost all of the boilerplate subscription billing code you are dreading writing. In addition to basic subscription management, Cashier can handle coupons, swapping subscription, subscription "quantities", cancellation grace periods, and even generate invoice PDFs.

## Official Documentation

Documentation for Cashier can be found on the [Laravel website](http://laravel.com/docs/billing).

## This Fork - Stripe Connect

This fork of Cashier allows you to use some of Stripe's Connect functionality. To use this package, you should add it as a repository in your composer.json:

```bash
"repositories": [
    {
        "type": "vcs",
        "url": "https://github.com/keithbrink/cashier"
    }
]
```

and then update the Cashier package to use the connect branch of this package:

```bash
"require": {
    "laravel/cashier": "dev-connect"
}
```

Once installed, you can use Cashier like normal, but you can add a billing account:

```bash
$user->billingAccount($account_id)->subscription('main');
```

and an application fee can be added to a subscription:

```bash
$user
    ->billingAccount($account_id)
    ->newSubscription('main', $subscription_id)
    ->applicationFeePercent($application_fee_percent)
    ->create($token);
```

## Running Cashier's Tests Locally

You will need to set the following details locally and on your Stripe account in order to run the Cashier unit tests:

### Environment

#### .env

    STRIPE_SECRET=
    STRIPE_CONNECT_ACCOUNT_ID=
    STRIPE_MODEL=Laravel\Cashier\Tests\Fixtures\User

You can set these variables in the `phpunit.xml` file.

### Stripe

Add the following information to your Stripe account:

#### Plans

    * monthly-10-1 ($10)
    * monthly-10-2 ($10)

#### Coupons

    * coupon-1 ($5)

## Contributing

Thank you for considering contributing to the Cashier. You can read the contribution guide lines [here](contributing.md).

## License

Laravel Cashier is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).
