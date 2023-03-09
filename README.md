# spark-history-server

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![AppVersion: 3.0.1](https://img.shields.io/badge/AppVersion-3.0.1-informational?style=flat-square)

# Spark history server Helm Chart

[SHS](https://apache-spark-on-k8s.github.io/userdocs/running-on-kubernetes.html) Spark History Server is the web UI for completed and running Spark applications.

## Chart Details

This chart uses AWS K8s [IRSA](https://aws.amazon.com/blogs/opensource/introducing-fine-grained-iam-roles-service-accounts/) technology to authenticate against AWS, so a proper `ServiceAccount` needs to be specified in order to have the right permissions accessing application logs S3 bucket.

## Installing the Chart

To install the chart:

```sh
helm install --set app.S3logPath=yourBucketName/eventLogFoloder
```

## Required variables

Minimum required variables are:
* `S3LogPath` - S3 path to read logs from
* `serviceAccount.name` - Service account name with proper permissions to access S3 bucket

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| S3logPath | string | `"my-company-s3-bucket/spark-hs"` | S3 path to read logs from |
| affinity | object | `{}` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"bitnami/spark"` |  |
| image.tag | string | `"3.0.1"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.enabled | bool | `false` |  |
| ingress.host | string | `"spark.example.io"` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| service.externalPort | int | `80` |  |
| service.internalPort | int | `18080` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.create | bool | `false` |  |
| serviceAccount.name | string | `"sa-with-s3-access"` |  |
| spark.credProviderString | string | `""` |  |
| spark.maxFilesToRetain | string | `""` |  |
| tolerations | list | `[]` |  |

