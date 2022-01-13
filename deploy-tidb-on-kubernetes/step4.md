
### 4.1. TiDBをインストールするNamespaceを作成
`kubectl create namespace tidb-cluster`{{execute}}

例:

```shell
controlplane $ kubectl create namespace tidb-cluster
namespace/tidb-cluster created
```

### 4.2. TiDBをインストールするNamespaceを作成
`kubectl create -f https://raw.githubusercontent.com/pingcap/tidb-operator/master/examples/basic/tidb-cluster.yaml -n tidb-cluster`{{execute}}

例:

```shell
controlplane $ kubectl create -f https://raw.githubusercontent.com/pingcap/tidb-operator/master/examples/basic/tidb-cluster.yaml -n tidb-cluster
tidbcluster.pingcap.com/basic created
```

### 4.3. TiDBのデプロイ結果を確認
`kubectl get tc -n tidb-cluster`{{execute}}

例:

```shell
controlplane $ kubectl get tc -n tidb-cluster
NAME    READY   PD    STORAGE   READY   DESIRE   TIKV   STORAGE   READY   DESIRE   TIDB   READY   DESIRE   AGE
basic   False         1Gi               1               1Gi               1                       1        3s
```

`basic-discovery`, `basic-pd`, `basic-tikv`と`basic-tidb`は`Running`の状態になれば、TiDBクラスターが正常に稼働しています

`kubectl get pod -n tidb-cluster`{{execute}}

例:

```shell
controlplane $ kubectl get pod -n tidb-cluster
NAME                               READY   STATUS    RESTARTS   AGE
basic-discovery-5b677d7997-ps29t   1/1     Running   0          3m29s
basic-pd-0                         1/1     Running   0          3m28s
basic-tidb-0                       2/2     Running   0          60s
basic-tikv-0                       1/1     Running   0          105s
```
