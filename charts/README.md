# charts

_[Helm](https://helm.sh) charts for [`api`][api]._

## Installation

You can install these charts from the repository located at `https://charts.darylwalsh.me`.

```bash
## Add the repository.
helm repo add darylwalsh https://charts.darylwalsh.me

## Install the chart.
helm install -f values.yaml -n api darylwalsh/api
```

## Configuration

See
[`api/values.yaml`](https://github.com/darylwalsh/api/blob/master/deployment/charts/api/values.yaml)
for an the default `values.yaml` configuration.

To install `api` for production, one should have an Ingress controller in
the target namespace, and configure a `values.yaml` with an appropriate
`ingress.host` value:

```yaml
ingress:
  host: api.darylwalsh.me # example
```

[api]: https://github.com/darylwalsh/merlin
