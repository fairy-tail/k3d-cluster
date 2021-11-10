# k3d-cluster
k3d 集群

## 安装 k3d

``` sh
brew install k3d
```

## 创建一个多节点集群并映射到宿主机端口 8080

``` sh
k3d cluster create k3d -p "8080:80@loadbalancer" --agents 2
```

## 部署 nginx 应用测试集群

``` sh
kubectl create deployment nginx --image=nginx
kubectl create service clusterip nginx --tcp=80:80
kubectl apply -f nginx-ingress.yaml
```

## 测试 nginx 应用

``` sh
curl localhost:8080
```
