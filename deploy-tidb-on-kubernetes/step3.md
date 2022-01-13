
### 3.1. TiDB CRDのデプロイ
`kubectl create -f https://raw.githubusercontent.com/pingcap/tidb-operator/master/manifests/crd.yaml`{{execute}}

例:

```shell
controlplane $ kubectl apply -f https://raw.githubusercontent.com/pingcap/tidb-operator/master/manifests/crd.yaml
customresourcedefinition.apiextensions.k8s.io/backups.pingcap.com created
customresourcedefinition.apiextensions.k8s.io/backupschedules.pingcap.com created
customresourcedefinition.apiextensions.k8s.io/dmclusters.pingcap.com created
customresourcedefinition.apiextensions.k8s.io/restores.pingcap.com created
customresourcedefinition.apiextensions.k8s.io/tidbclusterautoscalers.pingcap.com created
customresourcedefinition.apiextensions.k8s.io/tidbclusters.pingcap.com created
customresourcedefinition.apiextensions.k8s.io/tidbinitializers.pingcap.com created
customresourcedefinition.apiextensions.k8s.io/tidbmonitors.pingcap.com created
customresourcedefinition.apiextensions.k8s.io/tidbngmonitorings.pingcap.com created
```

### 3.2. HelmでTiDB OperatorのRepoを追加
`helm repo add pingcap https://charts.pingcap.org/`{{execute}}

例:

```shell
controlplane $ helm repo add pingcap https://charts.pingcap.org/
"pingcap" has been added to your repositories
```

### 3.3. TiDB OperatorをインストールするNamespaceを作成
`kubectl create namespace tidb-admin`{{execute}}

例:

```shell
controlplane $ kubectl create namespace tidb-admin
namespace/tidb-admin created
```

### 3.4. HelmでインストールできるTiDB Operatorのバージョンを確認
`helm search repo tidb-operator --versions`{{execute}}

例:

```shell
controlplane $ helm search repo tidb-operator --versions
NAME                    CHART VERSION   APP VERSION     DESCRIPTION                            
pingcap/tidb-operator   v1.2.6          v1.2.6          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.2.5          v1.2.5          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.2.4          v1.2.4          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.2.3          v1.2.3          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.2.2          v1.2.2          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.2.1          v1.2.1          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.2.0          v1.2.0          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.14         v1.1.14         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.13         v1.1.13         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.12         v1.1.12         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.11         v1.1.11         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.10         v1.1.10         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.9          v1.1.9          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.8          v1.1.8          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.7          v1.1.7          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.6          v1.1.6          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.5          v1.1.5          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.4          v1.1.4          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.3                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.2                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.1                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.0                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.7                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.6                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.5                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.4                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.3                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.2                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.1                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.0                          tidb-operator Helm chart for Kubernetes
```

### 3.5. HelmでTiDB Operatorをデプロイ
`helm install --namespace tidb-admin tidb-operator pingcap/tidb-operator --version v1.2.4`{{execute}}

例:

```shell
controlplane $ helm install --namespace tidb-admin tidb-operator pingcap/tidb-operator --version v1.2.4
NAME: tidb-operator
LAST DEPLOYED: Wed Jan 12 03:27:17 2022
NAMESPACE: tidb-admin
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
Make sure tidb-operator components are running:

    kubectl get pods --namespace tidb-admin -l app.kubernetes.io/instance=tidb-operator
```

### 3.6. TiDB Operatorのデプロイ結果を確認
`tidb-controller-manager`と`tidb-scheduler`は`Running`の状態になれば、TiDB Operatorが正常に稼働しています。

`kubectl get pods --namespace tidb-admin`{{execute}}

例:

```shell
controlplane $ kubectl get pods --namespace tidb-admin 
NAME                                       READY   STATUS    RESTARTS   AGE
tidb-controller-manager-759c67f44f-xsswl   1/1     Running   0          17s
tidb-scheduler-6bc6cb78d4-lpqxz            2/2     Running   0          17s
```
