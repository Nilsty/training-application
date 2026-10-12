# Training Application Helm Chart

## Prerequisites for the value `persistMetaInfo`

- The StorageClass with the name `my-storageclass` has to exist in the cluster

## Prerequisites for the value `ingress.enabled`

- The IngressClass with the name `nginx` has to exist in the cluster
- CertManager has to exist in the cluster
- The ClusterIssuer with the name `letsencrypt-issuer` has to exist in the cluster

## Prerequisites for the value `gateway.enabled`

- Gateway API CRDs must be installed in the cluster (Gateway, HTTPRoute, GatewayClass, ...)
- A Gateway implementation (for example: Envoy Gateway, Contour, Istio) must be installed and a `Gateway` resource must exist which the chart can reference via `gateway.name` / `gateway.namespace`.

Notes:
- When `ingress.enabled` is `true` the chart will render a Kubernetes `Ingress` resource (compatible with ingress-nginx).
- When `gateway.enabled` is `true` the chart will render a `HTTPRoute` resource (Gateway API) that targets the service `my-app`.
- Only one option should be enabled.
