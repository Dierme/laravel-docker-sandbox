# Laravel on Docker
Demo application that puts laravel framework on docker

### Installation guide
Clone the project.  
Create a .env file `cp laravel-demo/.env.example laravel-demo/.env`  

```
$ docker-compose up --build   # build and start the project
$ docker-compose exec laravel-demo composer install   # install dependancies
$ docker-compose exec laravel-demo php artisan key:generate   # generate encryption key
$ docker-compose exec laravel-demo php artisan config:clear
$ docker-compose exec laravel-demo php artisan config:cache
```

