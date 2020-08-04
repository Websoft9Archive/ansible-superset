# CLI

Superset have CLI `superset` for administrator.  

Use **SSH** to login Server, and run the following command to Superset container

```
docker exec -it superset_superset_1 /bin/bash
```

Main options and commands:  

```
Usage: superset [OPTIONS] COMMAND [ARGS]...

  This is a management script for the Superset application.

Options:
  --version  Show the flask version
  --help     Show this message and exit.

Commands:
  db                        Perform database migrations.
  export-dashboards         Export dashboards to JSON
  export-datasource-schema  Export datasource YAML schema to stdout
  export-datasources        Export datasources to YAML
  fab                       FAB flask group commands
  flower                    Runs a Celery Flower web server Celery Flower
                            is...

  import-dashboards         Import dashboards from JSON
  import-datasources        Import datasources from YAML
  init                      Inits the Superset application
  load-examples             Loads a set of Slices and Dashboards and a...
  load-test-users           Loads admin, alpha, and gamma user for testing...
  refresh-druid             Refresh druid datasources
  routes                    Show the routes for the app.
  run                       Run a development server.
  set-database-uri          Updates a database connection URI
  shell                     Run a shell in the app context.
  sync-tags                 Rebuilds special tags (owner, type, favorited...
  update-datasources-cache  Refresh sqllab datasources cache
  version                   Prints the current version number
  worker                    Starts a Superset worker for async SQL query...
```