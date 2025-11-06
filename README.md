# MongoDB Blueprint

### Install using Krateo Composable Operation

Install the CompositionDefinition for the *Blueprint*:

```sh
cat <<EOF | kubectl apply -f -
apiVersion: core.krateo.io/v1alpha1
kind: CompositionDefinition
metadata:
  name: cloud-native-mongodb
  namespace: cloudnative-test
spec:
  chart:
    repo: mongodb
    url: https://marketplace.krateo.io
    version: 0.1.0
EOF
```