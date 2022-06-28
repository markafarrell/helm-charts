# route53-dynamic-dns

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![AppVersion: 1.2.1](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

route53-dynamic-dns helm package

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/markafarrell/helm-charts/issues/new/choose)**

## Source Code

* <https://github.com/sjmayotte/route53-dynamic-dns/>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.3.0 |

## TL;DR

```console
helm repo add markafarrell https://markafarrell.github.io/charts/
helm repo update
helm install route53-dynamic-dns markafarrell/route53-dynamic-dns
```

## IAM Role
Create an IAM user with the following policy

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "route53:ChangeResourceRecordSets",
                "route53:TestDNSAnswer"
            ],
            "Resource": "arn:aws:route53:::hostedzone/*"
        }
    ]
}
```

## Installing the Chart

To install the chart with the release name `route53-dynamic-dns`

```console
helm install route53-dynamic-dns markafarrell/route53-dynamic-dns
```

## Uninstalling the Chart

To uninstall the `route53-dynamic-dns` deployment

```console
helm uninstall route53-dynamic-dns
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install route53-dynamic-dns \
  --set env.TZ="America/New York" \
    markafarrell/route53-dynamic-dns
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install route53-dynamic-dns markafarrell/route53-dynamic-dns -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env | object | See below | environment variables. See more environment variables in the [route53-dynamic-dns documentation](https://sjmayotte.dev/route53-dynamic-dns/config/env/). |
| env.ROUTE53_HOSTED_ZONE_ID  | string | `""` | Hosted Zone for domain to be updated |
| env.ROUTE53_DOMAIN | string | `""` | Set the Domain Name to update |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"route53-dynamic-dns/route53-dynamic-dns"` | image repository |
| image.tag | string | `"v1.2.1"` | image tag |

## Changelog

### Version 1.0.0

#### Added

- Initial version

#### Changed

N/A

#### Fixed

N/A

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
