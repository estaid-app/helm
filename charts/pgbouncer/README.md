# pgBouncer Helm Chart

> This chart deploys a [pgBouncer](https://www.pgbouncer.org/) instance to Kubernetes.

## Description
This Helm chart deploys pgbouncer on Kubernetes, providing a highly efficient connection pooler for PostgreSQL database. It's designed to reduce the processing time and resources required by managing a large number of client connections to PostgreSQL servers.

## Chart Details

- **Chart Version:** 1.0.7
- **App Version:** 1.22.0
- **Kubernetes Version:** >= 1.20.0-0

## Installing the Chart
To install the chart with the release name `my-release`:

```bash
helm repo add estaid-app https://estaid-app.github.io/helm
helm install my-release estaid-app/pgbouncer
```

## Configuration

The following table lists the configurable parameters of the pgbouncer chart and their default values.

| Parameter                                     | Description                                                                                                          | Default                               |
|-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------|---------------------------------------|
| `replicaCount`                                | Replica count for the Deployment                                                                                     | `1`                                   |
| `nameOverride`                                | Override name of the deployment                                                                                      | `""`                                  |
| `fullnameOverride`                            | Override the full name of the deployment                                                                             | `""`                                  |
| `updateStrategy`                              | The update strategy to apply to the Deployment (Recreate/RollingUpdate)                                              | `{}`                                  |
| `updateStrategy.type`                         | Type of update strategy                                                                                              | `RollingUpdate` or `Recreate`         |
| `updateStrategy.rollingUpdate`                | The rolling update configuration                                                                                     | `{}`                                  |
| `updateStrategy.rollingUpdate.maxUnavailable` | The maximum number of pods that can be unavailable during the update                                                 | `1`                                   |
| `updateStrategy.rollingUpdate.maxSurge`       | The maximum number of pods that can be scheduled above the desired number of pods                                    | `25%`                                 |
| `minReadySeconds`                             | Minimum number of seconds for which a newly created pod should be ready                                              | `0`                                   |
| `revisionHistoryLimit`                        | The number of old ReplicaSets to retain to allow rollback                                                            | `10`                                  |
| `imagePullSecrets`                            | Optional array of imagePullSecrets containing private registry credentials                                           | `[]`                                  |
| `image.registry`                              | Container image registry                                                                                             | `""`                                  |
| `image.repository`                            | Container image repository                                                                                           | `ghcr.io/estaid-app/pgbouncer-docker` |
| `image.tag`                                   | Container image tag                                                                                                  | `1.22.0`                              |
| `image.pullPolicy`                            | Image pull policy                                                                                                    | `IfNotPresent`                        |
| `service.type`                                | Service type                                                                                                         | `ClusterIP`                           |
| `service.port`                                | Service port                                                                                                         | `5432`                                |
| `podLabels`                                   | Labels to add to the pod metadata                                                                                    | `{}`                                  |
| `podAnnotations`                              | Annotations to add to the pod metadata                                                                               | `{}`                                  |
| `extraEnvs`                                   | Additional environment variables to set                                                                              | `[]`                                  |
| `resources`                                   | Pod resources for scheduling/limiting                                                                                | `{}`                                  |
| `nodeSelector`                                | Node labels for pod assignment                                                                                       | `{}`                                  |
| `lifecycle`                                   | Lifecycle hooks                                                                                                      | `{}`                                  |
| `tolerations`                                 | Tolerations for pod assignment                                                                                       | `[]`                                  |
| `affinity`                                    | Affinity and anti-affinity                                                                                           | `{}`                                  |
| `priorityClassName`                           | Priority of pods                                                                                                     | `""`                                  |
| `runtimeClassName`                            | Runtime class for pods                                                                                               | `""`                                  |
| `pgbouncer`                                   | [Configuration specific to pgbouncer.](https://www.pgbouncer.org/config.html)                                        | `{}`                                  |
| `databases`                                   | [Database configuration for connection pooling.](https://www.pgbouncer.org/config.html#section-databases)            | `{}`                                  |
| `userlist`                                    | List of users allowed to connect through pgbouncer. See [auth_file](https://www.pgbouncer.org/config.html#auth_file) | `{}`                                  |
| `extraContainers`                             | Additional containers to be added to the pods                                                                        | `[]`                                  |
| `extraInitContainers`                         | Containers, which are run before the app containers are started                                                      | `[]`                                  |
| `extraVolumeMounts`                           | Additional volumeMounts to the main container                                                                        | `[]`                                  |
| `extraVolumes`                                | Additional volumes to the pods                                                                                       | `[]`                                  |
| `podDisruptionBudget.enabled`                 | If a PodDisruptionBudget resource is created                                                                         | `false`                               |
| `serviceAccount.name`                         | Name of the Service Account                                                                                          | `""`                                  |
| `serviceAccount.annotations`                  | Annotations for created Service Account                                                                              | `{}`                                  |
| `terminationGracePeriodSeconds`               | Termination grace period (in seconds)                                                                                | `60`                                  |

## License

[MIT](../../LICENSE)