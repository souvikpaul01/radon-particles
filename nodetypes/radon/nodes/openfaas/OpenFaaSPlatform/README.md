## OpenFaaS Platform

A node type that represents an externally managed OpenFaaS Platform.

| Name | URI | Version | Derived From |
|:---- |:--- |:------- |:------------ |
| `OpenFaaSPlatform` | `radon.nodes.opefaas.OpenFaaSPlatform` | 1.0.0 | `radon.nodes.abstract.CloudPlatform` |

In the following, the properties, attributes, capabilities, and requirements changed from / added to the parent type are listed:

### Properties

| Name | Required | Type | Constraint | Default Value | Description |
|:---- |:-------- |:---- |:---------- |:------------- |:----------- |
| `kubernetes_version` | `false` | `version` | N/A | 1.8 | The version of the Kubernetes cluster hosting this platform. |
| `basic_auth_user` | `true` | `string` | N/A | N/A | The username used for basic authentication. |
| `basic_auth_password` | `true` | `string` | N/A | N/A | The password used for basic authentication. |
| `api_gateway_host` | `true` | `string` | N/A | N/A | The host name to access OpenFaaS API gateway at. |
| `api_gateway_port` | `true` | `integer` | N/A | 31112 | The port to access OpenFaaS API gateway at. |
| `prometheus_port` | `true` | `integer` | N/A | 31119 | The port to access the Prometheus service at. |

### Attributes

| Name | Type | Default Value | Description |
|:---- |:---- |:------------- |:----------- |
| `url` | `string` | `concat: ["http://", get_property: [SELF, api_gateway_host], get_property: [SELF, api_gateway_port] ]` | The full gateway url. |

### Capabilities

| Name | Type | Valid Source Types | Occurrences |
|:---- |:---- |:------------------ |:----------- |
|`host`| `tosca.capabilities.Container` | `radon.nodes.openfaas.OpenFaasFunction` | [0,UNBOUNDED]

### Notes

* Parameters added to the `Standard` interface operations:
    * `create`: `KUBERNETES_VERSION`
    * `configure`: `URL`, `BASIC_AUTH_USER`, `BASIC_AUTH_PASSWORD`

---