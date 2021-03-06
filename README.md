<p align="center">
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://github.com/yiisoft.png" height="100px">
    </a>
    <h1 align="center">Yii application template</h1>
    <br>
</p>

[![Latest Stable Version](https://poser.pugx.org/yiisoft/app/v/stable.png)](https://packagist.org/packages/yiisoft/app)
[![Total Downloads](https://poser.pugx.org/yiisoft/app/downloads.png)](https://packagist.org/packages/yiisoft/app)
[![build](https://github.com/yiisoft/app/workflows/build/badge.svg)](https://github.com/yiisoft/app/actions)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/yiisoft/app/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/yiisoft/app/?branch=master)
[![Code Coverage](https://scrutinizer-ci.com/g/yiisoft/app/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/yiisoft/app/?branch=master)

<p align="center">
    <a href="https://github.com/yiisoft/app" target="_blank">
        <img src="docs/images/home.png" alt="Home page" >
    </a>
</p>

Yii application template for Yii 3 is best for rapidly creating projects.

## Requirements

The minimum requirement by this project template that your Web server supports PHP 7.4.0.

## Installation

If you do not have [Composer](http://getcomposer.org/), you may install it by following the instructions
at [getcomposer.org](http://getcomposer.org/doc/00-intro.md).

You can then install this project template using the following command:

```
composer create-project --prefer-dist --stability dev yiisoft/app <your project>
```

In order to launch development web server run:

```
composer run serve
```

Now you should be able to access the application through the URL printed to console.
Usually it is `http://localhost:8080`.

## Directory structure

```
config/             application configurations
resources/layout    layout files for the web application
resources/view      view files for the web application
app/                application directory
    Asset/          assets definition
    Controller/     Web controller classes
    Factory/        factory classes files for config
    Provider/       provider classes for config
runtime/            files generated during runtime
tests/              various tests for the basic application
vendor/             dependent 3rd-party packages      
public/             the entry script and Web resources
```

## Configuration

You can find configuration in `config` directory. There are multiple
configs, and the most interesting is `params.php`.

### Application Components

#### Aliases

```php
'aliases' => [
    // standard directory aliases
    '@root' => dirname(__DIR__),
    '@assets' => '@root/public/assets',
    '@assetsUrl' => '/assets',
    '@npm' => '@root/node_modules',
    '@public' => '@root/public',
    '@resources' => '@root/resources',
    '@runtime' => '@root/runtime',
    '@views' => '@root/resources/views'
],
```

#### Cache

```php
'yiisoft/cache-file' => [
    'file-cache' => [
        // cache directory path
        'path' => '@runtime/cache'
    ],
],
```

#### Log Target File

```php
use Psr\Log\LogLevel;

'yiisoft/log-target-file' => [
    'file-target' => [
        // route directory file log
        'file' => '@runtime/logs/app.log',
        // levels logs target
        'levels' => [
            LogLevel::EMERGENCY,
            LogLevel::ERROR,
            LogLevel::WARNING,
            LogLevel::INFO,
            LogLevel::DEBUG,
        ],
    ],
    'file-rotator' => [
        // maximum file size, in kilo-bytes. Defaults to 10240, meaning 10MB.
        'maxfilesize' => 10,
        // number of files used for rotation. Defaults to 5.
        'maxfiles' => 5,
        // the permission to be set for newly created files.
        'filemode' => null,
        // Whether to rotate files by copy and truncate in contrast to rotation by renaming files.
        'rotatebycopy' => null
    ],
],
```

#### Session

```php
'yiisoft/yii-web' => [
    'session' => [
        // options for cookies
        'options' => ['cookie_secure' => 0],
        // session handler
        'handler' => null
    ],
],
```

##### Yii Debug

```php
'yiisoft/yii-debug' => [
    // enabled/disabled debugger
    'enabled' => true
],
```

#### Application Layout Parameters

```php
'app' => [
    'brandurl' => '/',
    'charset' => 'UTF-8',
    'hero.options' => ['class' => 'hero is-fullheight is-light'],
    'hero.head.options' => ['class' => 'hero-head has-background-black'],
    'hero.body.options' => ['class' => 'hero-body is-light'],
    'hero.container.options' => ['class' => 'container has-text-centered'],
    'hero.footer.options' => ['class' => 'hero-footer has-background-black'],
    'hero.footer.column.options' => ['class' => 'columns is-mobile'],
    'hero.footer.column.left' => 'Left',
    'hero.footer.column.left.options' => ['class' => 'column has-text-left has-text-light'],
    'hero.footer.column.center' => 'Center',
    'hero.footer.column.center.options' => ['class' => 'column has-text-centered has-text-light'],
    'hero.footer.column.right' => 'Right',
    'hero.footer.column.right.options' => ['class' => 'column has-text-right has-text-light'],
    'language' => 'en',
    'logo' => '/images/yii-logo.jpg',
    'name' => 'My Project',
    'navbar.options' => ['class' => 'navbar'],
    'navbar.brand.options' => ['class' => 'navbar-brand'],
    'navbar.brand.logo.options' => ['class' => 'navbar-item'],
    'navbar.brand.title.options' => ['class' => 'navbar-item has-text-light'],
],
```

## Testing

The template comes with ready to use [Codeception](https://codeception.com/) configuration.
In order to execute tests run:

```
composer run serve > ./runtime/yii.log 2>&1 &
vendor/bin/codecept run
```
