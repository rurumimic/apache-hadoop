# Hadoop 2.9.0

Helm: [Hadoop Chart 2.9.0](https://hub.kubeapps.com/charts/stable/hadoop)

## Install

```bash
helm repo add gradiant https://gradiant.github.io/charts
helm install hdfs gradiant/hdfs
```

### Describe

```bash
kubectl describe pod/hdfs-namenode-0 -n default
```

### Port forward

```bash
kubectl port-forward -n default hdfs-namenode-0 50070:50070
```

Open `http://localhost:50070`

### Pods

```bash
kubectl get pod

NAME                            READY   STATUS    RESTARTS   AGE
hdfs-datanode-0                 1/1     Running   0          2m37s
hdfs-datanode-1                 1/1     Running   0          92s
hdfs-datanode-2                 1/1     Running   0          78s
hdfs-httpfs-7b57cfd6d7-p6vmz    1/1     Running   0          2m37s
hdfs-namenode-0                 2/2     Running   0          2m37s
```

## Usage

```bash
kubectl exec -n default -it hdfs-namenode-0 -- hdfs dfs -ls /
```

```bash
kubectl exec -n default -it hdfs-namenode-0 -- hdfs dfs -mkdir -p /user/hdfs
```

```bash
kubectl exec -n default -it hdfs-namenode-0 -- hdfs dfs -ls -R /
```

```bash
kubectl port-forward -n default hdfs-namenode-0 8020:8020
```