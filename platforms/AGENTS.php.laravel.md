# PHP/Laravel Platform Guide

This document provides guidelines for working on Laravel projects. For comprehensive information, always refer to the [official Laravel documentation](https://laravel.com/docs).

## 1. Core Concepts

- **Service Container & Providers:** Manage dependencies and bootstrap the app. Located in `app/Providers`.
- **Eloquent ORM:** The default ActiveRecord ORM. Models are in `app/Models`.
- **Blade:** The templating engine. Views are in `resources/views`.
- **Artisan:** The command-line interface. Use `php artisan list` to see all commands.

## 2. Key Directories

- `app/`: Core application code (Controllers, Models, Providers).
- `config/`: Application configuration files.
- `database/`: Migrations, seeders, and factories.
- `public/`: Web server document root and public assets.
- `resources/`: Views, raw assets (JS/SASS), and language files.
- `routes/`: Route definitions (`web.php`, `api.php`).
- `tests/`: Automated tests (`Feature/`, `Unit/`).

## 3. Development Workflow

- **Create a feature:**
  1.  Define a route (`routes/web.php`).
  2.  Create a controller method (`app/Http/Controllers`).
  3.  Create a Blade view (`resources/views`).
  4.  Create a model and migration if needed (`php artisan make:model`, `php artisan make:migration`).
- **Run migrations:** `php artisan migrate`
- **Run tests:** `php artisan test` (or `./vendor/bin/pest`). All new code requires tests.
