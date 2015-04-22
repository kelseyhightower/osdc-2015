# Demo

## Provisioning

```
fleetctl list-machines
```

### Start Flannel

```
fleetctl start units/flannel.service
```

### Start Docker

``` 
fleetctl start units/docker.service
```

### Start Kubernetes Server Components

``` 
fleetctl start units/kube-etcd.service 
fleetctl start units/kube-apiserver.service 
fleetctl start units/kube-controller-manager.service 
fleetctl start units/kube-scheduler.service 
```

### Start Kubernetes Worker Components 

```
fleetctl start units/kube-kubelet.service 
fleetctl start units/kube-proxy.service
```

### Register Worker Nodes

``` 
fleetctl start units/kube-register.service 
```

## Deploy pgview stack

### Create the postgres pod

```
kubectl create -f pods/postgres.json
```

### Create the postgres service

```
kubectl create -f services/postgres.json
```

```
psql -h POSTGRES_PORTAL_IP -U postgres
```

### Create the pgview replication controller

```
kubectl create -f replicationcontrollers/pgview-stable-v1.json
```

### Create the pgview service

```
kubectl create -f services/pgview.json
```

```
curl http://PGVIEW_PORTAL_IP -d @rpc/version.json
```

```
curl http://PGVIEW_PORTAL_IP -d @rpc/sqlfeatures.json
```

Run it again, request should be served from memcache

```
curl http://PGVIEW_PORTAL_IP -d @rpc/sqlfeatures.json
```

#### Terminal 2

```
while true; do curl http://PGVIEW_PORTAL_IP -d @rpc/version.json; sleep 1; done
```

## Scaling pgview 

```
kubectl resize --replicas=3 replicationcontrollers pgview-stable-v1
```

## Upgrade pgview using the canary pattern

### Deploy the canary pod

```
kubectl create -f replicationcontrollers/pgview-canary.json
```

### Rolling upgrade

```
kubectl rolling-update --update-period=4s pgview-stable-v1 -f replicationcontrollers/pgview-stable-v2.json
```
