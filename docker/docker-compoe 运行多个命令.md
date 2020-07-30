# docker-compose 运行多个命令


```bash
docker-compose exec php sh -c 'cd blueprint; ls; composer install; php artisan horizon'
```

