
## Data sources

Once inside the UI, we need to declare four data sources, elasticsearch, sqlite, infinity from github, and infinity from s3.

On the left hand side, click on the burger menu icon to expand the menu.

Under "Connections" click to "Add new connection".

### SQlite

Search for slite and click install. Once the plugin is installed, click on "Add new data source", and set the following:

| name | value                    |
| ---- | ------------------------ |
| Name | sqlite                   |
| Path | /gtq.sqlite              |

### Elasticsearch

Search for elasticsearch. No need to install the plugin as it is there by default. Add a new data source and set the fields:

| name                            | value                                 |
| ----                            | -----                                 |
| Name                            | elasticsearch                         |
| URL                             | https://elasticsearch:9200            |
| Authentication                  | Basic authentication                  |
| User                            | elastic                               |
| Password                        | The password from installation step 2 |
| Skip TLS certificate validation | clicked                               |
| Index name                      | gtd                                   |
| Time field name                 | timestamp                             |

### Infinity - github
Search infinity and click install. Once the plugin is installed, click on "Add new data source", and set the following:

| name           | value                                                                                   |
| ----           | -----                                                                                   |
| Name           | gtd                                                                                     |
| Authentication | No Auth                                                                                 |
| Base URL       | https://raw.githubusercontent.com/elimayost/grafana-demo/refs/heads/master/data/gtd.csv |
| Health check   | Enable with same base URL                                                               |

### Infinity - S3
Click on "Add new data source", and set the following:

| name          | value                            |
| ----          | -----                            |
| Name          | cleversafe                       |
| Auth type     | AWS                              |
| Service       | s3                               |
| Access Key    |                                  |
| Secret Key    |                                  |
| Allowed hosts | https://s3.futureplc.engineering |
| Base URL      | https://s3.futureplc.engineering |

