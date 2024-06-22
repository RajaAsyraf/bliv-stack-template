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

## Installation (with Docker)
Ensure you have installed Docker (or Docker Desktop) in your local machine.
1. Run `./vendor/bin/sail up -d` to spin up the docker container.
2. You may use the available sail commands as [documented](https://laravel.com/docs/11.x/sail).
3. You may also attach to the container to execute the laravel commands as below:
 - Run `docker exec -it bliv-stack-template-laravel.test-1 bash`.
 - Run `php artisan key:generate`.
 - Run `php artisan migrate`.
 - Run `npm i && npm run dev`.
4. In browser, access the page via `http://localhost:80/`.


## Contribution
Feel free to submit a PR to improve this and let me know if you have better idea for this repo. Thanks!
