## Getting started with Docker

Make sure [Docker](https://www.docker.com) is installed and running on your environment.

Start with your local environment:
```sh
cp .env.example .env
```

Set a database name, user, password. Generate keys needed for Wordpress.

Build containers:
```sh
docker-compose build --no-cache
```

Run containers:
```sh
docker-compose up -d
```

Install Wordpress distribution:
```sh
docker-compose exec wp composer install
```

Your Wordpress site will be available upon `http://wp-test.localhost` url. You can change it via `WP_HOST` environment variable.

## Issues

- Files installed by composer owned to `root:root`
- Give write permissions for uploading media: `chmod 777 web/app/uploads`


