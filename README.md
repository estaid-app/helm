# Estaid Helm Charts 

[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/estaid)](https://artifacthub.io/packages/search?repo=estaid)


## Available Charts

- [pgBouncer](https://estaid-app.github.io/helm/charts/pgbouncer): A lightweight connection pooler for PostgreSQL.

## Usage

To use the Estaid Helm repository, you need to add it to your Helm repositories:

```bash
helm repo add estaid-app https://estaid-app.github.io/helm
helm repo update
```

You can then install any of the charts using the `helm install` command. For example, to install pgBouncer:

```bash
helm install my-release estaid-app/pgbouncer
```

## License

[MIT](LICENSE)