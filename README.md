# Laravel 10

This project has been created to experiment with **Laravel version 10**.

## Packages

The following packages have been used:

- [Laravel jetstream](https://jetstream.laravel.com/2.x/introduction.html) - Authentication starter kit. Livewire
  version, including Teams.
- [Filament PHP](https://filamentphp.com/docs/2.x/admin/installation) - Admin panel.

### Dev Tooling

- [Easy Coding Standard (ECS)](https://github.com/symplify/easy-coding-standard) - Preferred coding standard for this
  project, set to PSR-12 plus other standards. Pint is also an option for coding standards.
- [Larastan](https://github.com/nunomaduro/larastan) - Static analysis for Laravel using PhpStan.
- [Parallel-Lint](https://github.com/php-parallel-lint/PHP-Parallel-Lint) - This application checks syntax of PHP files
  in parallel
- [IDE helper](https://github.com/barryvdh/laravel-ide-helper) - helper for IDE auto-completion
- [Laravel debug bar](https://github.com/barryvdh/laravel-debugbar) - debug bar for views, shows models, db calls etc.
- [CaptainHook](https://github.com/captainhookphp/captainhook) - pre-commit hook to run the above tools before
  committing code

## Requirements

This is a Laravel 10 project. The requirements are the same as a
new [Laravel 10 project](https://laravel.com/docs/10.x).

- [8.1+](https://www.php.net/downloads.php)
- [Composer](https://getcomposer.org)

Recommended:

- [Git](https://git-scm.com/downloads)

## Clone

Clone the project repository

e.g.

```sh
git clone git@gitlab.com:heiw/laravel/laravel10.git
```

## Install

Install all the dependencies using composer

```sh
cd laravel10
composer install
```

## Create .env

Create an `.env` file from `.env.example`

```shell script
cp .env.example .env
```

## Configure Laravel

This project uses models and seeders to generate the tables for the database. Tests will use the seeded data. Configure
the Laravel **.env** file with the **database**, updating **username** and**password** as per you local setup.

```text
APP_NAME="laravel v10"

APP_URL=https://laravel10.test

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel10
DB_USERNAME=YourDatabaseUserName (root)
DB_PASSWORD=YourDatabaseUserPassword

MAIL_MAILER=log
```

## Generate APP_KEY

Generate an APP_KEY using the artisan command

```shell script
php artisan key:generate
```

## Create the database

The database will need to be manually created e.g.

```shell
mysql -u YourDatabaseUserName (root)
CREATE DATABASE laravel10 CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
exit
```

## Install Database

This project uses models and seeders to generate the tables for the database. Tests will use the seeded data.

```shell
php artisan migrate --seed
# or if previously migrated: 
php artisan migrate:fresh --seed 
```

## Vite

The first time you pull the project run install:

```shell
npm install
```

Compile your CSS / JavaScript for development and recompile on change:

```shell
npm run dev
```

When ready to deploy, compile your CSS / JavaScript for production:

```shell
npm run build
```

## Run tests

⚠️ The project has been configured to run tests using a **sqlite** in memory database. The PDO sqlite extension will
need to be enabled to run the tests. Alternatively amend the **phpunit.xml** to change this configuration.

To make it easy to run all the PHPUnit tests a composer script has been created in **composer.json**. From the root of
the projects, run:

```shell script
composer tests
```

You should see the results in testDoc format:

```text
> phpunit
PHPUnit 10.0.19 by Sebastian Bergmann and contributors.

Runtime:       PHP 8.1.16
Configuration: <your directory>\laravel10\phpunit.xml

..                                                 2 / 2 (100%)

Time: 00:00.131, Memory: 24.00 MB

Example (Tests\Unit\Example)
 ✔ That true is true

Example (Tests\Feature\Example)
 ✔ The application returns a successful response

OK (2 tests, 2 assertions)
```

## Code standard

Easy Coding Standard (ECS) is used to check for style and code standards, [PSR-12](https://www.php-fig.org/psr/psr-12/)
is used. Regularly run code standard checks to automatically clean up your code. In particular run before committing any
code.

To make it easy to run Easy Coding Standard (ECS) a composer script has been created in **composer.json**. From the root
of the projects, run:

```shell script
composer check-cs
```

You should see the results:

```text
 [OK] No errors found. Great job - your code is shiny in style!
```

If there are any warning, ECS will advise you to run --fix to fix them, this also has a composer script:

```shell
composer fix-cs
```

Sometimes the fix command needs to be run several times, as one fix will identify more problems, keep running the fix-cs
until you get the OK message.

## Static Analysis

PhpStan is used to run static analysis checks. Larastan has been installed, which is PhpStan and Laravel rules.
Regularly run static analysis checks to help identify problems. In particular run before committing any code.

To make it easy to run PhpStan a composer script has been created in **composer.json**. From the root of the project
run:

```shell script
composer phpstan
```

You should see the results:

```text

[OK] No errors

```

If PhpStan identifies any problems then review and fix them one by one. See
the [documentation for help](https://phpstan.org/user-guide/getting-started).

If the problem is related to third party code, it's possible to ignore this type of error:

```shell
composer phpstan-baseline
```

This will generate a **phpstan-baseline.neon** file, which should be added to version control. Only run this command
once other PhpStan errors have been fixed!

## Commit hook

[CaptainHook](https://github.com/captainhookphp/captainhook) has been installed and configured to run a pre-commit hook,
when you `git commit` any code ECS, PhpStan, Parallel lint and PHPUnit will be automatically run, if any of these fail
the commit will be rejected. You can always write a rule to bypass the failing code, but it is better to fix the
problem.

To install the hooks:

```shell
vendor/bin/captainhook install
```

Answer yes to all the questions, the **captainhook.json** config will take care of the hooks that run.

## IDE Helper

- [Laravel IDE Helper Generator](https://github.com/barryvdh/laravel-ide-helper)

To help autocompletion in PhpStorm Laravel IDE helper has been installed, to update models run:

```shell
composer ide
```

## Contributing

This is a **personal project**. Contributions are not required. Anyone interested in developing this project are welcome
to fork or clone for your own use.

## Credits

- Michael Pritchard (AKA Pen-y-Fan).

## Troubleshooting

The minimum required version of PHP is 8.1.0, if you try to run command lines with a lower PHP version you will receive
an error advising the minimum version. The workaround is to temporarily set the PATH to the version of PHP:

```shell
php -v
# PHP 7.4.19 (cli) (built: May  4 2021 14:24:38) ( ZTS Visual C++ 2017 x64 )
set PATH=C:\laragon\bin\php\php-8.1.10-Win32-vs16-x64\;%PATH%
php -v
# PHP 8.1.10 (cli) (built: Aug 30 2022 18:05:49) (ZTS Visual C++ 2019 x64)
```
