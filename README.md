# laravel-docker-boilerplate
Laravel boilerplate with Docker development environment (apache, node, mysql, elasticsearch)

### Usage

- Create laravel project
- Copy this folder on your project
- Update .env file
- Build the containers

```bash
docker-compose up -d
```

### Building specific containers
```bash
docker-compose build --no-cache apache
```

### ssh to a container ex. node
```bash
docker-compose exec node bash
```
