# clamav

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![AppVersion: 0.104.2](https://img.shields.io/badge/AppVersion-0.104.2-informational?style=flat-square)

ClamAV® is an open source antivirus engine for detecting trojans, viruses, malware & other malicious threats.

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/Cisco-Talos/clamav>
* <https://hub.docker.com/r/clamav/clamav>
* <https://docs.clamav.net/>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.3.0 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install clamav k8s-at-home/clamav
```

## Installing the Chart

To install the chart with the release name `clamav`

```console
helm install clamav k8s-at-home/clamav
```

## Uninstalling the Chart

To uninstall the `clamav` deployment

```console
helm uninstall clamav
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install clamav \
  --set env.TZ="America/New York" \
    k8s-at-home/clamav
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install clamav k8s-at-home/clamav -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env.CLAMAV_NO_CLAMD | bool | `false` |  |
| env.CLAMAV_NO_FRESHCLAMD | bool | `false` |  |
| env.CLAMAV_NO_MILTERD | bool | `true` |  |
| env.CLAMD_STARTUP_TIMEOUT | int | `1800` |  |
| env.FRESHCLAM_CHECKS | int | `1` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"tccr.io/truecharts/clamav"` |  |
| image.tag | string | `"v0.104.2@sha256:eb816a62ce0b7c331d893e8d51e54fe96b1cb5878c7394e935a48468b0b44f6d"` |  |
| persistence.sigdatabase.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.sigdatabase.enabled | bool | `true` |  |
| persistence.sigdatabase.mountPath | string | `"/var/lib/clamav"` |  |
| persistence.sigdatabase.size | string | `"256Mi"` |  |
| podSecurityContext.runAsGroup | int | `0` |  |
| podSecurityContext.runAsUser | int | `0` |  |
| probes.liveness.custom | bool | `true` |  |
| probes.liveness.enabled | bool | `true` |  |
| probes.liveness.spec.exec.command[0] | string | `"clamdcheck.sh"` |  |
| probes.liveness.spec.failureThreshold | int | `10` |  |
| probes.liveness.spec.initialDelaySeconds | int | `15` |  |
| probes.liveness.spec.periodSeconds | int | `30` |  |
| probes.liveness.spec.timeoutSeconds | int | `1` |  |
| probes.readiness.custom | bool | `true` |  |
| probes.readiness.enabled | bool | `true` |  |
| probes.readiness.spec.exec.command[0] | string | `"clamdcheck.sh"` |  |
| probes.readiness.spec.failureThreshold | int | `10` |  |
| probes.readiness.spec.initialDelaySeconds | int | `15` |  |
| probes.readiness.spec.periodSeconds | int | `30` |  |
| probes.readiness.spec.timeoutSeconds | int | `1` |  |
| probes.startup.custom | bool | `true` |  |
| probes.startup.enabled | bool | `true` |  |
| probes.startup.spec.exec.command[0] | string | `"clamdcheck.sh"` |  |
| probes.startup.spec.failureThreshold | int | `10` |  |
| probes.startup.spec.initialDelaySeconds | int | `15` |  |
| probes.startup.spec.periodSeconds | int | `30` |  |
| probes.startup.spec.timeoutSeconds | int | `1` |  |
| securityContext.readOnlyRootFilesystem | bool | `false` |  |
| securityContext.runAsNonRoot | bool | `false` |  |
| service.main.ports.main.port | int | `3310` |  |
| service.main.ports.main.targetPort | int | `3310` |  |
| service.milter.enabled | bool | `true` |  |
| service.milter.ports.milter.enabled | bool | `true` |  |
| service.milter.ports.milter.port | int | `7357` |  |
| service.milter.ports.milter.targetPort | int | `7357` |  |

## Changelog

### Version 1.0.0

### Older versions

A historical overview of changes can be found on [ArtifactHUB](https://artifacthub.io/packages/helm/k8s-at-home/clamav?modal=changelog)

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v0.1.1](https://github.com/k8s-at-home/helm-docs/releases/v0.1.1)
