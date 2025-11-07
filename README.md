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

### Install using Krateo Composable Portal

```sh
cat <<EOF | kubectl apply -f -
apiVersion: core.krateo.io/v1alpha1
kind: CompositionDefinition
metadata:
  name: portal-blueprint-page
  namespace: krateo-system
spec:
  chart:
    repo: portal-blueprint-page
    url: https://marketplace.krateo.io
    version: 1.0.5
EOF
```

Install the Blueprint using, as metadata.name, the *Blueprint* name (the Helm Chart name of the blueprint):

```sh
cat <<EOF | kubectl apply -f -
apiVersion: composition.krateo.io/v1-0-5
kind: PortalBlueprintPage
metadata:
  name: mongodb
  namespace: cloudnative-test
spec:
  blueprint:
    url: https://marketplace.krateo.io
    version: 0.1.0 # this is the Blueprint version
    hasPage: true
  form:
    alphabeticalOrder: false
  panel:
    title: MongoDB
    icon:
      name: "fa-solid fa-file"
EOF
```