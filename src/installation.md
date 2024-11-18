
## Installation

### Tools needed

- Docker
- docker-compose
- [Task](https://taskfile.dev/)

### Install

1. Clone the repository:

``` bash
git clone git@github.com:efmayost/grafana-demo.git
```

2. Launch the required containers:

``` bash
docker-compose up
```

3. Create a .env file with the following:

``` bash
USERNAME=elastic
PASSWORD='XXXXXXXXXXXXXX'
INDEX_NAME= gtd
```

4. Change the elastic user's password:

``` bash
docker exec -it elasticsearch elasticsearch-reset-password -u elastic
```

5. Create the elasticesearch gtd index:

``` bash
task create-index:run
```

6. Add the processors for that index:

``` bash
task add-processors:run
```

7. Ingest the data:

``` bash
task ingest:run
```

8. Verify the total docs count (shoul be ~ 180K):

``` bash
task count-docs:run
```

9. Copy the sqlite database file to grafana container:

``` bash
docker cp data/gtd.sqlite grafana:/
```

### Grafana UI

In your browser open [UI](http://localhost:3000)

Username: admin Password: admin

You can skip updating the password.
