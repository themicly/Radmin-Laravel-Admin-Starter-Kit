## [Radmin - Laravel Admin starter with REST API User Roles Permission](https://codecanyon.net/item/laravel-admin-template-roles-permission-editable-datatables/26005211) v3.4.0
<img src="https://github.com/RakibDevs/Radmin-Laravel-Admin-starter-with-REST-API-User-Roles-Permission/blob/main/radmin.jpg">


[Radmin](https://codecanyon.net/item/laravel-admin-template-roles-permission-editable-datatables/26005211) is a premium template starter kit including REST API, Advanced user, roles & permission management , Serverside Datatable, Datatable Edit and Export( CSV, EXCEL, PRINT, PDF, COPY),Cache Clear, XSS protection and many more features.

Buy this premium starter kit [here](https://codecanyon.net/item/laravel-admin-template-roles-permission-editable-datatables/26005211)

### v3.4.0 Release Notes
- 🐳 Added guideline and configuration for running inside docker container. 

## Run inside Docker 🐳
Before running Laravel inside Docker, please make sure you have installed `docker`.

1. Copy environment, docker-compose and Dockerfile

```bash
cp .env.docker.example .env
cp docker-conf/php/local.example docker-conf/php/Dockerfile
cp docker-compose.yml.example docker-compose.yml
```

2. Run the following command to build the Docker image:
```bash
docker compose build
```
This command will download all the necessary dependencies and build the Docker image according to the specifications in the Dockerfile.

3. Once the build is complete, run the following command to start the Docker container: 
```bash
docker-compose up -d
```

4. Run migration and seeder to migrate database. Note this command will refresh your databse also.
```bash
docker compose exec php php artisan migrate:refresh --seed
```
If you dont wan't to refresh databse run
```bash
docker compose exec php php artisan migrate --seed
```
5. Once done, you can visit your website at http://localhost:8900/


If you are using old version, Click to see [Laravel 9 Upgrade Guideline](https://github.com/themicly/Radmin-Laravel-Admin-Starter-Kit/blob/main/upgrade-to-laravel-9.md)

<a href="https://www.producthunt.com/posts/radmin-laravel-dashboard-starter?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-radmin&#0045;laravel&#0045;dashboard&#0045;starter" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=384432&theme=light" alt="Radmin&#0032;&#0045;&#0032;Laravel&#0032;Dashboard&#0032;Starter - Take&#0032;your&#0032;dashboard&#0032;to&#0032;the&#0032;next&#0032;level&#0033; | Product Hunt" style="width: 250px; height: 54px;" width="250" height="54" /></a>

