# Plex Media Server helm chart

## Configuration

The following tables lists the configurable parameters of the Plex chart and their default values.

| Parameter                  | Description                         | Default                                                 |
|----------------------------|-------------------------------------|---------------------------------------------------------|
| `image.repository`         | Image repository | `plexinc/pms-docker` |
| `image.tag`                | Image tag. Possible values listed [here](https://hub.docker.com/r/plexinc/pms-docker/tags/).| `1.16.0.1226-7eb2c8f6f`|
| `image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `kubePlex.enabled`         | Enable KubPlex transcoder | `true` |
| `kubePlex.image.repository`         | Image repository | `ghcr.io/ressu/kube-plex` |
| `kubePlex.image.tag`                | Image tag. | `latest`|
| `kubePlex.image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `claimToken`                 | Plex Claim Token to authenticate your acount | `` |
| `timezone`                 | Timezone plex instance should run as, e.g. 'America/New_York' | `Europe/London` |
| `extraEnv`                 | Extra Environment variables to set, e.g. 'puid,pgid' | `[]` |
| `runtimeClassName`         | Run time class name, e.g. 'nvidia' | `` |
| `service.type`          | Kubernetes service type for the plex GUI/API | `ClusterIP` |
| `service.port`          | Kubernetes port where the plex GUI/API is exposed| `32400` |
| `service.annotations`   | Service annotations for the Plex GUI | `{}` |
| `service.labels`        | Custom labels | `{}` |
| `service.loadBalancerIP` | Load balancer IP for the Plex GUI; set `service.type` to `LoadBalancer` to use this. | `{}` |
| `service.loadBalancerSourceRanges` | List of IP CIDRs allowed access to load balancer (if supported)      | None |
| `probes.liveness.custom` | Set this to `true` if you wish to specify your own livenessProbe | `false` |
| `probes.liveness.enabled` | Enable the liveness probe | `true` |
| `probes.liveness.spec` | The spec field contains the values for the default livenessProbe. If you selected `custom: true`, this field holds the definition of the livenessProbe. | `` |
| `probes.readiness.custom` | Set this to `true` if you wish to specify your own readinessProbe | `false` |
| `probes.readiness.enabled` | Enable the readiness probe | `true` |
| `probes.readiness.spec` | The spec field contains the values for the default readinessProbe. If you selected `custom: true`, this field holds the definition of the readinessProbe. | `` |
| `probes.startup.custom` | Set this to `true` if you wish to specify your own startupProbe | `false` |
| `probes.startup.enabled` | Enable the startup probe | `true` |
| `probes.startup.spec` | The spec field contains the values for the default startupProbe. If you selected `custom: true`, this field holds the definition of the startupProbe. |
| `ingress.enabled`              | Enables Ingress | `false` |
| `ingress.annotations`          | Ingress annotations | `{}` |
| `ingress.labels`               | Custom labels | `{}` |
| `ingress.path`                 | Ingress path | `/` |
| `ingress.hosts`                | Ingress accepted hostnames | `chart-example.local` |
| `ingress.tls`                  | Ingress TLS configuration | `[]` |
| `rbac.create`                  | Create RBAC roles? | `true` |
| `nodeSelector`             | Node labels for pod assignment | `kubernetes.io/arch: amd64` |
| `persistence.transcode.enabled`      | Use persistent volume for transcoding | `false` |
| `persistence.transcode.size`         | Size of persistent volume claim | `20Gi` |
| `persistence.transcode.claimName`| Use an existing PVC to persist data | `nil` |
| `persistence.transcode.subPath` | SubPath to use for existing Claim | `nil` |
| `persistence.transcode.storageClass` | Type of persistent volume claim | `-` |
| `persistence.transcode.accessMode` | Persistent volume access mode | `ReadWriteMany` |
| `persistence.data.size`         | Size of persistent volume claim | `40Gi` |
| `persistence.data.claimName`| Use an existing PVC to persist data | `nil` |
| `persistence.data.subPath` | SubPath to use for existing Claim | `nil` |
| `persistence.data.storageClass` | Type of persistent volume claim | `-` |
| `persistence.data.accessMode` | Persistent volume access mode | `ReadWriteMany` |
| `persistence.extraData` | Extra data mounts.  Should be an array of items matching persistence.data entries | `[]` |
| `persistence.config.size`         | Size of persistent volume claim | `20Gi` |
| `persistence.config.claimName`| Use an existing PVC to persist data | `nil` |
| `persistence.config.subPath` | SubPath to use for existing Claim | `nil` |
| `persistence.config.storageClass` | Type of persistent volume claim | `-` |
| `persistence.config.accessMode` | Persistent volume access mode | `ReadWriteMany` |
| `resources`                | CPU/Memory resource requests/limits | `{}` |
| `proxy.enable`           | use to enable PMS proxy environmental variable  | `{false}` |
| `proxy.http`           | HTTP_PROXY value 'http://proxy.lan:8080'  | `{}` |
| `proxy.https`           | HTTPS_PROXY value 'http://proxy.lan:8080'  | `{}` |
| `proxy.noproxy`           | NO_PROXY value 'localhost,127.0.0.1,10.96.0.0/12,10.244.0.0/12'  | `{}` |
| `tolerations`           | Pod tolerations  | `[]` |
| `affinity`           | Pod affinity configuration  | `{}` |
| `podAnnotations`           | Key-value pairs to add as pod annotations  | `{}` |
| `deploymentAnnotations`           | Key-value pairs to add as deployment annotations  | `{}` |

Read through the [values.yaml](values.yaml) file. It has several commented out suggested values.
