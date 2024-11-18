
## Data sources

Once inside the UI, we need to declare three data sources, elasticsearch, and sqlite.

On the left hand side, click on the burger menu icon to expand the menu.

Under "Connections" click to "Add new connection".

### SQlite

Search for slite and click install. Once the plugin is installed, click on "Add new data source", and set the following:

- Name: sqlite Path: /gtq.sqlite

### Elasticsearch

Search for elasticsearch. No need to install the plugin as it is there by default. Add a new data source and set the fields:

- Name: elasticsearch
- URL: https://elasticsearch:9200
- Authentication: Basic authentication
- User: elastic
- Password: The password from installation step 2
- Skip TLS certificate validation: clicked
- Index name: gtd
- Time field name: timestamp

### Infinity
Search for slite and click install. Once the plugin is installed, click on "Add new data source", and set the following:

- Name: gtd
- Authentication: No Auth
- Base URL: https://raw.githubusercontent.com/elimayost/grafana-demo/refs/heads/master/data/gtd.csv
- Health check: Enable with same base URL

