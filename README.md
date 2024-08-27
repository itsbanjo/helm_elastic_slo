# My-App Helm Chart

This Helm chart deploys a simple Nginx application with a customizable greeting and sets up an SLO (Service Level Objective) dashboard in Elasticsearch.

## Prerequisites

- Kubernetes 1.16+
- Helm 3.0+
- Elasticsearch 8.0+ (for SLO dashboard)

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
helm install my-release .
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
helm delete my-release
```

## Configuration

The following table lists the configurable parameters of the chart and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of replicas for the Nginx deployment | `1` |
| `image.repository` | Nginx image repository | `nginx` |
| `image.tag` | Nginx image tag | `latest` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `service.type` | Kubernetes Service type | `ClusterIP` |
| `service.port` | Kubernetes Service port | `80` |
| `customerName` | Customer name for the greeting | `"Default Customer"` |
| `elasticSearch.host` | Elasticsearch host URL | `"http://elasticsearch-master:9200"` |
| `elasticSearch.username` | Elasticsearch username | `"elastic"` |
| `elasticSearch.password` | Elasticsearch password | `"changeme"` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```bash
helm install my-release . --set customerName="John Doe"
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example:

```bash
helm install my-release -f values.yaml .
```

## SLO Dashboard

This chart includes a job that creates an SLO dashboard in Elasticsearch. The SLO configuration is defined in the `templates/slo-job.yaml` file. You can customize the SLO parameters by modifying this file.

## Customizing the Nginx Configuration

To customize the Nginx configuration, you can modify the `templates/configmap.yaml` file. This file creates a ConfigMap that can be used to override the default Nginx configuration.

## Troubleshooting

If you encounter any issues while installing or using this chart, please check the following:

1. Ensure that your Kubernetes cluster is running and that you have the necessary permissions.
2. Verify that Helm is properly installed and configured.
3. Check that the Elasticsearch instance is accessible and that the credentials are correct.

For more detailed debugging, you can use the `--debug` flag with Helm commands:

```bash
helm install my-release . --debug
```

If you need further assistance, please open an issue in the project repository.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
