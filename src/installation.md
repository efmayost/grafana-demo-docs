
## Installation

### Tools needed

- Docker
- docker-compose
- [Task](https://taskfile.dev/)

### Install

1. Launch the required containers:

``` bash
docker-compose up
```

2. Create a .env file with the following:

``` bash
USERNAME=elastic
PASSWORD='XXXXXXXXXXXXXX'
INDEX_NAME= gtd
```

3. Change the elastic user's password:

``` bash
docker exec -it elasticsearch elasticsearch-reset-password -u elastic
```

4. Create the elasticesearch gtd index:

``` bash
task create-index:run
```

5. Add the processors for that index:

``` bash
task add-processors:run
```

6. Ingest the data:

``` bash
task ingest:run
```

7. Verify the total docs count (shoul be ~ 180K):

``` bash
task count-docs:run
```

8. Copy the sqlite database file to grafana container:

``` bash
docker cp data/gtd.sqlite grafana:/
```

### Grafana UI

In your browser open [UI](http://localhost:3000)

Username: admin Password: admin

You can skip updating the password.
