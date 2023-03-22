# rockapp
test helm charts
#Create pod with generated crds over flux cli as below
```
flux create source helm charts  --url=https://raimundasr.github.io/rockapp/charts --namespace rock --interval=10s --export | tee rock-hrepo.yaml


flux create helmrelease rockapp \
    --interval=10m \
    --source=HelmRepository/charts\
    --chart=rockapp \
    --namespace rock \
    --interval=10s \
    --export | tee rock-crd.yaml
```


#Or you can add with helm repo add

```
helm repo add rockapp https://raimundasr.github.io/rockapp/
```

```
helm install my-rock-app rockapp/rockapp --version=0.1.0
```

#Charts yaml

there are verison specified where means as docker tag from dockerhub registry

```
appVersion: "1.16.0"
```

THIS IS FROM Charts.yml

```
apiVersion: v2
name: rockapp
description: A Helm chart for Kubernetes

# A chart can be either an 'application' or a 'library' chart.
#
# Application charts are a collection of templates that can be packaged into versioned archives
# to be deployed.
#
# Library charts provide useful utilities or functions for the chart developer. They're included as
# a dependency of application charts to inject those utilities and functions into the rendering
# pipeline. Library charts do not define any templates and therefore cannot be deployed.
type: application

# This is the chart version. This version number should be incremented each time you make changes
# to the chart and its templates, including the app version.
# Versions are expected to follow Semantic Versioning (https://semver.org/)
version: 0.1.0

# This is the version number of the application being deployed. This version number should be
# incremented each time you make changes to the application. Versions are not expected to
# follow Semantic Versioning. They should reflect the version the application is using.
# It is recommended to use it with quotes.
appVersion: "1.16.0"
```
