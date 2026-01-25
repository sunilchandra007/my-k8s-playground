# Helm Cheatsheet

- Helm is a package manager for Kubernetes that simplifies deploying and managing applications using *charts*.
- Helm Chart is bundle of YAML files that can be downloaded from Helm repository.
- It is based on templates/blueprint with placeholders for dynamic values from values.yaml or --set command

https://helm.sh/docs/intro/cheatsheet/
---
  
## Core Concepts
- **Chart**: A package of pre-configured Kubernetes resources.
- **Release**: An instance of a chart deployed/running in a Kubernetes cluster.
- **Repository**: A collection of charts or storage location for charts.
- **Values**: Default configuration settings for a chart, defined in `values.yaml`.

---

## Repository Management ( local cache/machine )
 
```bash
# Add a new chart repository to local helm client
helm repo add <repo-name> <repo-url>
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add apisix https://charts.apiseven.com

# List/Update/remove repositories in local cache

# list all the existing repository
helm repo list
helm repo update
helm repo remove <repo-name>

# search for chart/app in helm repository
helm search repo apisix
helm search repo <keyword> # Search added repositories for a keyword in charts
helm search hub <keyword> # Search for charts in the Artifact Hub or your own hub instance

# display default values of helm chart
helm show values apisix/apisix
helm show readme apisix/apisix

# View a list of all installed plugins
helm plugin list       
```


## Managing Releases ( in k8s namespace / cluster )
  
```bash
# List all deployed releases in current namespace
helm list -all --date --deployed --pending --failed --uninstalled --superseded 

# Retrieve information such as values/manifest/notes about a release
helm get all <release-name>
helm get hooks <release-name> 
helm get values <release-name>
helm get manifest <release-name>
helm get notes <release-name>

# Install/Upgrade/uninstall a release in k8s cluster
helm install <release-name> <chart-name>
helm upgrade <release-name> <chart-name>

# uninstall helm release in k8s cluster
helm uninstall <release-name>
helm -n ingress-apisix delete apisix
helm -n ingress-apisix uninstall apisix
helm -n ingress-apisix uninstall apisix-dashboard
helm -n ingress-apisix list 

# View Release status/ History
helm status <release-name>
helm status <release-name> --revision <number>
helm history <release-name>
helm rollback <release-name> <revision>

```
