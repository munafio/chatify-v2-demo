# Chatify 2 Demo

A minimal Laravel app for trying [Chatify v2](https://github.com/munafio/chatify) (beta). Includes Laravel Breeze auth, two demo users, and the Chatify UI at `/chatify`.

## Requirements

- PHP 8.3+
- Composer
- Node.js 20+ and npm
- SQLite (default) or another Laravel-supported database

## Setup

### 1. Clone

```bash
git clone <repo-url> chatify2-demo
cd chatify2-demo
```

### 2. Install PHP dependencies

```bash
composer install
```

### 3. Create `.env` and configure options

```bash
cp .env.example .env
php artisan key:generate
```

Open `.env` and set the following as needed:

**Giphy** (optional — enables GIF search):

```env
CHATIFY_GIPHY_API_KEY=your_giphy_api_key
```

**WebSockets / real-time** (optional — typing, online status, instant delivery). Without this, messages still work but not realtime:

```env
BROADCAST_CONNECTION=pusher
PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_APP_CLUSTER=mt1
PUSHER_APP_USETLS=true
PUSHER_SCHEME=https
```

You can also use [Laravel Reverb](https://laravel.com/docs/reverb) instead of Pusher (`BROADCAST_CONNECTION=reverb` and the matching Reverb vars) or other ws drivers.

### 4. Database

SQLite is the default. Create the database file:

```bash
touch database/database.sqlite
```

Then migrate, seed demo users, and link storage:

```bash
php artisan migrate
php artisan db:seed
php artisan storage:link
```

### 5. Frontend assets

```bash
npm install
npm run build
```

### 6. Run the app

```bash
php artisan serve
```

Open [http://127.0.0.1:8000](http://127.0.0.1:8000), log in, then open **Messenger** or go to `/chatify`.

## Demo accounts


| Name  | Email                                         | Password |
| ----- | --------------------------------------------- | -------- |
| Alice | [alice@example.com](mailto:alice@example.com) | password |
| Bob   | [bob@example.com](mailto:bob@example.com)     | password |


Use two browsers (or normal + incognito) to chat between Alice and Bob.

## Notes

- **File uploads:** If attachments fail, set `upload_tmp_dir` in `php.ini` to a writable path such as `storage/framework/temp`.
- **Links:** [Chatify](https://github.com/munafio/chatify) · [Docs](https://chatify.munafio.com) · [Packagist](https://packagist.org/packages/munafio/chatify)

## License

MIT