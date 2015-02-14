Yii2-Config
===========
[![Code Climate](https://codeclimate.com/github/abhi1693/yii2-config/badges/gpa.svg)](https://codeclimate.com/github/abhi1693/yii2-config)
[![Latest Stable Version](https://poser.pugx.org/abhi1693/yii2-config/v/stable.svg)](https://packagist.org/packages/abhi1693/yii2-config) [![Total Downloads](https://poser.pugx.org/abhi1693/yii2-config/downloads.svg)](https://packagist.org/packages/abhi1693/yii2-config) [![Latest Unstable Version](https://poser.pugx.org/abhi1693/yii2-config/v/unstable.svg)](https://packagist.org/packages/abhi1693/yii2-config) [![License](https://poser.pugx.org/abhi1693/yii2-config/license.svg)](https://packagist.org/packages/abhi1693/yii2-config)

Yii2-Config provides a web interface for advanced configuration control and includes following features:

- Get Value from DB
- Set Value to DB
- Delete Value from DB
- Delete All Values from DB

Documentation
=============

## Installation

This document will guide you through the process of installing Yii2-Config using **composer**. Installation is a quick and
easy three-step process.

> **NOTE:** Before we start make sure that you have properly configured **db** application component.


Step 1: Download using composer
-------------------------------

Add Yii2-config to the require section of your **composer.json** file:

```php
{
    "require": {
        "abhi1693/yii2-config": "1.0.0"
    }
}
```

And run following command to download extension using **composer**:

```bash
$ php composer.phar update
```

Step 2: Configure your application
----------------------------------

```php
$config = [
    ...
    'components' => [
        ...
        'config' => [
            'class'         => 'abhimanyu\config\components\Config', // Class (Required)
            'db'            => 'db',                                 // Database Connection ID (Optional)
            'tableName'     => '{{%config}}',                        // Table Name (Optioanl)
            'cacheId'       => 'cache',                              // Cache Id. Defaults to NULL (Optional)
            'cacheKey'      => 'config.cache',                       // Key identifying the cache value (Required only if cacheId is set)
            'cacheDuration' => 100                                   // Cache Expiration time in seconds. 0 means never expire. Defaults to 0 (Optional)
        ]
    ]
]
```

Step 3: Updating database schema
--------------------------------

```bash
yii migrate/up --migrationPath=@vendor/abhi1693/yii2-config/migrations
```


## Basic Usage

Get
---
```php
Yii::$app->config->get('key1');
Yii::$app->config->get('key2', 'default');
Yii::$app->config->get(['key1' => 'value1']);
```

Set
---
```php
Yii::$app->config->set('key1', 'value1');
Yii::$app->config->set('key1', ['value1', 'value2']);
Yii::$app->config->set(['key1' => 'value1']);
```

Delete
------
```php
Yii::$app->config->delete('key1');
Yii::$app->config->deleteAll(); // delete all config
```

## CHANGE LOGS

Refer to [Change Logs](CHANGE.md)

#### How to contribute?

Contributing instructions are located in [CONTRIBUTING.md](CONTRIBUTING.md) file.

## License

Yii2-config is released under the MIT License. See the bundled [LICENSE](LICENSE) for details.
