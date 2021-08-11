# EBAY-SDK-PHP

**This repository is now actively maintained by Bibliopolis.**

This project enables PHP developers to use the [eBay API](https://go.developer.ebay.com/api-documentation) in their PHP code, and build software using services such as [Finding](http://developer.ebay.com/Devzone/finding/Concepts/FindingAPIGuide.html), [Trading](http://developer.ebay.com/DevZone/guides/ebayfeatures/index.html), [Shopping](http://developer.ebay.com/Devzone/shopping/docs/Concepts/ShoppingAPIGuide.html), etc. You can get started by [installing the SDK via Composer](http://devbay.net/sdk/guides/getting-started/installation.html) and by following the [Basic Usage Guide](http://devbay.net/sdk/guides/getting-started/basic-usage.html).

This is a project that has been developed by [David T. Sadler](http://twitter.com/davidtsadler). Bibliopolis has forked the code and will keep up to date. It is in no way endorsed, sponsored or maintained by eBay.

## Plans
  - Keep up to date with latest PHP version
  - Add latest features required to be an eBay Developer (as of now that is the Notification API)

## Features

  - Compatible with PHP 7.3 or greater.
  - Easy to install with [Composer](http://getcomposer.org/).
  - Compliant with [PSR-1](http://www.php-fig.org/psr/psr-1/), [PSR-2](http://www.php-fig.org/psr/psr-2/) and [PSR-4](http://www.php-fig.org/psr/psr-4/).

## Resources

  - [User Guides](http://devbay.net/sdk/guides/) - Getting started guide and in-depth information.
  - [Examples](https://github.com/davidtsadler/ebay-sdk-examples) - Several examples of using the SDK. Plans to fork and add new examples.

## Requirements

  - PHP 7.3 or greater with the following extensions:
      - cURL
      - libxml
  - 64 bit version of PHP recommended as there are some [issues when using the SDK with 32 bit](http://devbay.net/sdk/guides/getting-started/requirements.html#using-the-sdk-with-32-bit-systems).
  - SSL enabled on the cURL extension so that https requests can be made.

## Installation

The SDK can be installed with [Composer](http://getcomposer.org/). Please see the [Installation section of the User Guide](http://devbay.net/sdk/guides/getting-started/installation.html) to learn about installing through other means.

  1. Install Composer.

     ```
     curl -sS https://getcomposer.org/installer | php
     ```

  1. Install the SDK.

     ```
     php composer.phar require mattybaer/ebay-sdk-php
     ```

  1. Require Composer's autoloader by adding the following line to your code.

     ```php
     require 'vendor/autoload.php';
     ```

## Example

### Get public key

```php
<?php

require 'vendor/autoload.php';

use \DTS\eBaySDK\Notifcation\Services;
use \DTS\eBaySDK\Notifcation\Types;

// Fetch request headers from eBay
$headers = getallheaders();
$key = base64_decode($headers['x-ebay-signature']);

// Create the service object.
$service = new Services\NotificationService([
  'authorization' => <AUTHORIZATION_HERE>
]);

// Create the request object.
$request = new Types\GetPublicKeyRestRequest();
$request->public_key_id = $key;

// Send the request to the service operation.
$response = $service->getPublicKey($request);

// Output the result of calling the service operation.
printf("Your official eBay public key is: %s\n", print_r($response, true));
```

## License

Licensed under the [Apache Public License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).

Copyright 2016 [David T. Sadler](http://twitter.com/davidtsadler)
