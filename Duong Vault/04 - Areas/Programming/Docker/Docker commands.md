
```sh
# Chạy PostgreSQL docker image
docker run --name spring_pg -p 5433:5432 -e POSTGRES_PASSWORD=secret -e POSTGRES_USER=duong -e POSTGRES_DB=root postgres:12-alpine
```
