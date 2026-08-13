# unpoller

![Version: 3.0.0](https://img.shields.io/badge/Version-3.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v2.21.0](https://img.shields.io/badge/AppVersion-v2.21.0-informational?style=flat-square)

A Helm chart for unpoller, a unifi prometheus exporter. This chart helps deploy Unpoller (unifi metrics exporter)
in kubernetes clusters.
It crates a Deployment to run the unpoller container, confiuration is stored in a ConfigMap and mounted in the container.
It supports integration with Prometheus operator, so a PodMonitor is created that will scrape the Deployment for the metrics.
Optionally, it can deploy automatically the dashboards into a Grafana instance through the integration with GrafanaOperator:
* Creates a Grafana CR with the credentials provided (or reuses existing Grafana object)
* Creates a Dashboard instance for all the unpoller provided charts.

See further documentation in how to install unpoller in Kubernetes in http://unpoller.github.io/helm-chart

**Note**: *This is a best effort to keep this chart working for kubernetes.*

**Homepage:** <https://unpoller.com/>

## Source Code

* <https://github.com/unpoller/helm-chart>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| config.influxdb.disable | bool | `true` |  |
| config.loki.disable | bool | `true` |  |
| config.poller.debug | bool | `false` |  |
| config.poller.plugins | list | `[]` |  |
| config.poller.quiet | bool | `false` |  |
| config.prometheus.disable | bool | `false` |  |
| config.prometheus.http_listen | string | `"0.0.0.0:9130"` |  |
| config.prometheus.report_errors | bool | `false` |  |
| config.unifi.defaults.hash_pii | bool | `false` |  |
| config.unifi.defaults.pass | string | `"unifi"` |  |
| config.unifi.defaults.save_dpi | bool | `true` |  |
| config.unifi.defaults.save_ids | bool | `true` |  |
| config.unifi.defaults.save_sites | bool | `true` |  |
| config.unifi.defaults.sites[0] | string | `"all"` |  |
| config.unifi.defaults.url | string | `"https://unifi.home:8443"` |  |
| config.unifi.defaults.user | string | `"unifi"` |  |
| config.unifi.defaults.verify_ssl | bool | `false` |  |
| config.unifi.dynamic | bool | `false` |  |
| dashboards.create | bool | `true` |  |
| dashboards.grafana.create | bool | `true` |  |
| dashboards.grafana.secret.existingSecretName | string | `""` |  |
| dashboards.grafana.secret.password | string | `"prom-operator"` |  |
| dashboards.grafana.secret.username | string | `"admin"` |  |
| dashboards.grafana.selectorLabels | object | `{}` |  |
| dashboards.grafana.url | string | `""` |  |
| debug | bool | `false` |  |
| defaultCredentialsExistingSecret.enabled | bool | `false` |  |
| defaultCredentialsExistingSecret.name | string | `""` |  |
| defaultCredentialsExistingSecret.passwordKey | string | `"password"` |  |
| defaultCredentialsExistingSecret.userKey | string | `"user"` |  |
| extraEnv | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ghcr.io/unpoller/unpoller"` |  |
| image.tag | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| livenessProbe.httpGet.path | string | `"/"` |  |
| livenessProbe.httpGet.port | string | `"tcp"` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` |  |
| podMonitor.enabled | bool | `true` | Whether to create a PodMonitor resource for Prometheus Operator. Set to `false` if Prometheus Operator CRDs are not installed. |
| podSecurityContext | object | `{}` |  |
| readinessProbe.httpGet.path | string | `"/"` |  |
| readinessProbe.httpGet.port | string | `"tcp"` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.annotations | object | `{}` | Additional annotations for the Service (e.g., for Grafana Alloy autodiscovery) |
| service.enabled | bool | `false` | Whether to create a Service resource |
| service.port | int | `9130` | Service port for metrics endpoint |
| service.type | string | `"ClusterIP"` | Service type (ClusterIP, NodePort, LoadBalancer) |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.automount | bool | `true` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` |  |

