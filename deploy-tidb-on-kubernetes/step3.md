# 3. TiDB Operatorのデプロイ

### 3.1. TiDB CRDのデプロイ
<pre>
`kubectl create -f https://raw.githubusercontent.com/pingcap/tidb-operator/master/manifests/crd.yaml`{{copy}}
</pre>

実行例:
<pre>
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
</pre>

### 3.2. HelmでTiDB OperatorのRepoを追加
<pre>
`helm repo add pingcap https://charts.pingcap.org/`{{copy}}
</pre>

実行例:
<pre>
controlplane $ helm repo add pingcap https://charts.pingcap.org/
"pingcap" has been added to your repositories
</pre>

### 3.3. TiDB OperatorをインストールするNamespaceを作成
<pre>
`kubectl create namespace tidb-admin`{{copy}}
</pre>

実行例:
<pre>
controlplane $ kubectl create namespace tidb-admin
namespace/tidb-admin created
</pre>

### 3.4. HelmでインストールできるTiDB Operatorのバージョンを確認
<pre>
`helm search repo tidb-operator --versions`{{copy}}
</pre>

### 3.5. HelmでTiDB Operatorをデプロイ
<pre>
`helm install --namespace tidb-admin tidb-operator pingcap/tidb-operator --version v1.2.4`{{copy}}
</pre>

実行例:
<pre>
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
</pre>

### 3.6. TiDB Operatorのデプロイ結果を確認

`tidb-controller-manager`と`tidb-scheduler`は`Running`の状態になると、TiDB Operatorが正常に稼働になる事です。
<pre>
`kubectl get pods --namespace tidb-admin`{{copy}}
</pre>

実行例:
<pre>
controlplane $ kubectl get pods --namespace tidb-admin 
NAME                                       READY   STATUS    RESTARTS   AGE
tidb-controller-manager-759c67f44f-xsswl   1/1     Running   0          17s
tidb-scheduler-6bc6cb78d4-lpqxz            2/2     Running   0          17s
</pre>