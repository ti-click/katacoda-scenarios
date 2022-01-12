# 1. Kubernetes クラスターの確認

### 1.1. Kubernetes Config Fileの導入
<pre>
`export KUBE_CONFIG=.kube/config`{{copy}}
</pre>

Kubernetes Config Fileを導入しなかった場合、`kubectl`を実行する際に`error: no configuration has been provided, try setting KUBERNETES_MASTER environment variable`エラーが表示されます。

### 1.2. Kubernetes クラスターの状況を確認

<pre>
`kubectl get node`{{copy}}
</pre>

実行例:
<pre>
controlplane $ kubectl get node
NAME           STATUS   ROLES    AGE   VERSION
controlplane   Ready    master   57s   v1.18.0
node01         Ready    none     27s   v1.18.0
</pre>