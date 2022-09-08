# Example Chart

Sample Helm chart for an application with one HTTP interface (e.g., a website).

Copy [chart] and change:

- In [Chart.yaml], edit metadata such as `name`, `description`, `keywords`,
  `sources`, and `maintainers`.
- In [values.yaml], edit at least `image.repository` and `image.tag`.
- Optionally, if the image is listening on a port other than 80, edit the
  [container port][container-port].

All defined template names start with `app.` which
[should be changed][defined-templates] to a unique name (app name) with:

```shell
find chart/templates/ -type f -exec sed -i s/\"app\\./\"UNIQUE_NAME./g {} +
```

Features:

- Templating with `toYaml`, always. Prevents confusion of variable types.
- Alphabetical order of keys, but `name` always comes first.

## Installing

### Install to Kubernetes using Helm

Setup Helm repository:

```shell
helm repo add czetech https://charts.cze.tech/
```

Install Helm chart:

```shell
helm install example-chart czetech/example-chart \
  --set ingress.enabled=true \
  --set ingress.hosts[0]=HOST
```

see the [chart] for more options.

## Support

Professional support by Czetech is available at <hello@cze.tech>.

## Source code

The source code is available at <https://github.com/czetech/example-chart>.

[chart]: chart
[chart.yaml]: chart/Chart.yaml
[container-port]: chart/templates/http-deployment.yaml#L34
[defined-templates]: https://helm.sh/docs/chart_best_practices/templates/#names-of-defined-templates
[values.yaml]: chart/values.yaml
