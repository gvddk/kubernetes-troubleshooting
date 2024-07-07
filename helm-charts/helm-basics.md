### What is helm?
helm is a package manager for install, upgrade and rollback packages in kubernetes.

Ubunu - apt is a package manager
Redhat/Centos - Yum is a package manager

### Installing helm on MAC

brew install helm

### Create helm chart structure
helm create nginx-chart

### Terminology
* helm repository (centralized palce for helm charts)
* helm chart (package manifests files)

### How to search and install the charts in helm?
* helm repo add **REPO_URL**
* helm repo update (Ensure to have latest information of charts available in the local system)
* helm repo ls (listing repositories)
* helm search repo **REPO_NAME/** -l
```
helm search repo bitnami/external-dns -l (Displays all the versions)
helm search repo bitnami/external-dns (Only latest version)
```
* helm install *customRepoName* *chartName*
```
helm repo add cortex-helm https://cortexproject.github.io/cortex-helm-chart
helm install cortex cortex-helm/cortex -f cortex-values.yaml
```
* helm template --name-template=**TEMPLATE_NAME** .
* helm template abc bitnami/external-dns --values=values.yaml

## How to create helm chart templating structure
```
helm create <chart-name>
```

### Commands for pulling and pushing helm charts

* helm push
* helm pull **REPO_NAME/CHART_NAME** --version **VERSION_NUMBER**

### Commands for installing helm charts 
* helm install s3proxy edgeless/s3proxy --set awsAccessKeyID="$ACCESS_KEY" --set awsSecretAccessKey="$ACCESS_SECRET"


### _helpers.tpl file 
Helm helper file(.tpl) is also called "Partials". These files are basically “includes” that can be embedded into existing files while a Chart is being installed.

```
_my-common-configmap.tpl:

{{- define "my-common-configuration" -}}
# Environment
clusterEnv: {{ index .Values.global.clusterEnv .Values.global.env | quote }}
namespace: {{ index .Values.global.namespace .Values.global.env | quote }}

my-values.yaml
--
global:
  # env refers to the environment properties belong to during build-time. Default is "development".
  env: development
  clusterEnv:
    development: staging
    pre_production: preprod
  registry:
    development: dev-images
    pre_production: preprod-images


Microservice chart configmap:

apiVersion: v1
kind: ConfigMap
metadata:
  name: my-configmap-name
  namespace: {{ index .Values.global.namespace .Values.global.env }}
data:
  log_level: {{ index .Values.global.log_level .Values.global.env | quote }}
  ...
  ...
  ...
{{ include "my-common-configuration" . | indent 2 }}


Final output:
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-configmap-name
  namespace: dev
data:
  log_level: debug
  ...
  ...
  ...
  namespace: staging
  registry: dev-images
```

## References
https://devopscube.com/create-helm-chart/
