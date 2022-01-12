
### 2.1. Local Storageをデプロイ
`kubectl create -f https://raw.githubusercontent.com/ti-click/katacoda-scenarios/main/deploy-tidb-on-kubernetes/yaml/local-storage.yaml`{{execute}}

実行例:
```
controlplane $ kubectl apply -f https://raw.githubusercontent.com/ti-click/katacoda-scenarios/main/deploy-tidb-on-kubernetes/yaml/local-storage.yaml 
serviceaccount/local-path-provisioner-service-account created
clusterrole.rbac.authorization.k8s.io/local-path-provisioner-role created
clusterrolebinding.rbac.authorization.k8s.io/local-path-provisioner-bind created
deployment.apps/local-path-provisioner created
storageclass.storage.k8s.io/local-path created
configmap/local-path-config created
```

### 2. Local Storageをデプロイされた状況を確認

#### 2.1 Podの確認
`kubectl get pod -n kube-system`{{execute}}

実行例:
```
controlplane $ kubectl get pod -n kube-system
NAMESPACE     NAME                                      READY   STATUS    RESTARTS   AGE
kube-system   coredns-66bff467f8-82c5j                  1/1     Running   0          7m32s
kube-system   coredns-66bff467f8-nx9gz                  1/1     Running   0          7m32s
kube-system   etcd-controlplane                         1/1     Running   0          7m38s
kube-system   katacoda-cloud-provider-b695dbfbf-964hx   1/1     Running   4          7m32s
kube-system   kube-apiserver-controlplane               1/1     Running   0          7m38s
kube-system   kube-controller-manager-controlplane      1/1     Running   0          7m38s
kube-system   kube-flannel-ds-amd64-52fx6               1/1     Running   0          7m32s
kube-system   kube-flannel-ds-amd64-vdcfx               1/1     Running   0          7m22s
kube-system   kube-keepalived-vip-7kdcc                 1/1     Running   0          7m2s
kube-system   kube-proxy-c4gr6                          1/1     Running   0          7m32s
kube-system   kube-proxy-f4qcr                          1/1     Running   0          7m22s
kube-system   kube-scheduler-controlplane               1/1     Running   0          7m38s
kube-system   local-path-provisioner-55fb677577-2cwkw   1/1     Running   0          7s
```

#### 2.2 Storage Classの確認
`kubectl get sc`{{execute}}

実行例:
```
controlplane $ kubectl get sc
NAME                   PROVISIONER             RECLAIMPOLICY   VOLUMEBINDINGMODE      ALLOWVOLUMEEXPANSION   AGE
local-path (default)   rancher.io/local-path   Delete          WaitForFirstConsumer   false                  15s
```