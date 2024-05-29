### What is helm?
helm is a package manager for install, upgrade and rollback packages in kubernetes.

Ubunu - apt is a package manager
Redhat/Centos - Yum is a package manager

### Installing helm on MAC

brew install helm

### Terminology
* helm repository (centralized palce for helm charts)
* helm chart (package manifests files)

### How to search and install the charts in helm?
* helm repo add <customName> <repoName>
* helm search repo <customRepoName>
* helm install <customRepoName> <chartName>
* helm template <customName> helmChartName <Templating all manifest files as single file>

## How to create helm chart templating structure
```
helm create <chart-name>
```

### Commands for pulling and pushing helm charts

* helm push
* helm pull
