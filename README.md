## About BLIV Stack Template

This template repository is consist of these stacks:
1. Bootstrap 5 with Tabler UI
2. Laravel 11
3. Inertia
4. Vue 3

Optimization tools
1. Laravel Debugbar
2. Laravel Pulse

This is an alternative to VILT stack if you are keen to work with Bootstrap 5.

## Screenshots
These are the built-in pages that are ready to be used or modified as you like.
1. Sign in, sign up, forgor password pages
![login-page](/public/screenshots/login-page.png)

2. Dashboard page
![dashboard-page](/public/screenshots/dashboard-page.png)

3. Setting page
![setting-page](/public/screenshots/setting-page.png)

## Installation
Before run this in your local, make sure you have PHP 8, Composer and Node.js (for NPM) installed in your local machine. You may also consider using [Laravel Herd](https://herd.laravel.com). Once you have that ready, you can follow this steps:
1. Execute `composer install` to install all of the PHP packages.
2. Copy the `.env` file from `.env.example` using this command `cp .env.example .env`.
3. Generate the key `php artisan key:generate`.
4. Run the migration `php artisan migrate`. It will ask to configure SQLite database and answer `Y` (or enter) to create it.
5. Install JavaScript packages using `npm install`.
6. Finally, you can build the frontend using `npm run build`.


## Contribution
Feel free to submit a PR to improve this and let me know if you have better idea for this repo. Thanks!
