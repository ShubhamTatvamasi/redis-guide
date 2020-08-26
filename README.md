# redis-guide

create a redis server
```bash
kubectl run redis --image=redis --restart=Never --port=6379 --expose

kubectl patch svc redis \
  --patch='{"spec": {"type": "NodePort"}}'

kubectl patch svc redis \
  --patch='{"spec": {"ports": [{"nodePort": 30637, "port": 6379}]}}'
```

connect to redis server
```bash
NODE_NAME=$(kubectl get pod redis -o jsonpath='{.spec.nodeName}')

NODE_IP=$(kubectl get nodes ${NODE_NAME} \
  -o jsonpath='{.status.addresses[?(@.type=="ExternalIP")].address}')

redis-cli -h ${NODE_IP} -p 30637 -n 0

redis-cli -h k8s.shubhamtatvamasi.com -p 30637
```

delete deployment
```bash
kubectl delete pod/redis service/redis
```

---

### redis cli commands

set a key-value pair
```
SET apple 123
```

get key-value pair
```
GET apple
```

delete everything
```
FLUSHALL
```
