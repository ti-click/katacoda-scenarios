# 4. TiDBのデプロイ

### 4.1. TiDBをインストールするNamespaceを作成
<pre>
`kubectl create namespace tidb-cluster`{{copy}}
</pre>

実行例:
<pre>
controlplane $ kubectl create namespace tidb-cluster
namespace/tidb-cluster created
</pre>

### 4.2. TiDBをインストールするNamespaceを作成
<pre>
`kubectl create -f https://raw.githubusercontent.com/pingcap/tidb-operator/master/examples/basic/tidb-cluster.yaml -n tidb-cluster`{{copy}}
</pre>

実行例:
<pre>
controlplane $ kubectl create -f https://raw.githubusercontent.com/pingcap/tidb-operator/master/examples/basic/tidb-cluster.yaml -n tidb-cluster
tidbcluster.pingcap.com/basic created
</pre>

### 4.3. TiDBのデプロイ結果を確認
<pre>
`kubectl get tc -n tidb-cluster`{{copy}}
</pre>

実行例:
<pre>

</pre>

`basic-discovery`, `basic-pd`, `basic-tikv`と`basic-tidb`は`Running`の状態になると、TiDBクラスターが正常に稼働になる事です
<pre>
`kubectl get pod -n tidb-cluster`{{copy}}
</pre>

実行例:
<pre>
controlplane $ kubectl get pod -n tidb-cluster
NAME                               READY   STATUS    RESTARTS   AGE
basic-discovery-5b677d7997-ps29t   1/1     Running   0          3m29s
basic-pd-0                         1/1     Running   0          3m28s
basic-tidb-0                       2/2     Running   0          60s
basic-tikv-0                       1/1     Running   0          105s
</pre>