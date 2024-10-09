- Creating a laravel project using utility container : `docker-compose run --rm composer create-project --prefer-dist --ignore-platform-reqs laravel/laravel .`

- Laravel to Mysql Connection:  
    After project is created, open `/src/.env` and edit accordingly to the `mysql.env`
    ```
    DB_CONNECTION=mysql
    DB_HOST=mysql
    DB_PORT=3306
    DB_DATABASE=homestead
    DB_USERNAME=homestead
    DB_PASSWORD=secret
    ```

- Running project containers : `docker-compose up -d --build server`

- Artisan Migrate : `docker-compose run --rm artisan migrate`