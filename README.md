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

redis-cli -h ${NODE_IP} -p 30637
```
---

### redis cli commands


set and get key/value
```redis
set customer:1000 fred
get customer:1000
```
```redis
set customer:1500 jane
get customer:1500
```

get all keys
```redis
keys customer:1*
```

scan all keys
```redis
scan 0 MATCH customer:1*
```

delete keys
```redis
unlink customer:1000
```

check key existence
```redis
exists customer:1000
```

create a non existent key
```redis
set inventory:100-meters-womens-final 1000 NX
get inventory:100-meters-womens-final
set inventory:100-meters-womens-final "Sold out" NX
set inventory:100-meters-womens-final 0 XX
```
> NX: Not Existent, XX: Do Exist
---

set a key that will expire in 50 seconds
```redis
set seat-hold Row:A:Seat:4 PX 50000
set seat-hold Row:A:Seat:4 EX 50
get seat-hold
```

update the expire time to 1 second
```redis
pexpire seat-hold 1
```

set expire time and check time remaining
```redis
set seat-hold Row:A:Seat:4 EX 50
ttl seat-hold
```



---

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
