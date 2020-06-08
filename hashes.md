# hashes

create a hash set
```redis
hset event:judo capacity 12000 location "Nippon Budokan" ticket_price:gold 100 availability:gold 8000
```

check how many hash sets exist
```redis
hexists event:judo capacity
```

get get value from hash set
```redis
hget event:judo capacity
```

subtract 10 from hash value
```redis
hincrby event:judo availability:gold -10
hget event:judo availability:gold
```

get the values of all in hash set
```redis
hgetall event:judo
```

add another key/value in hash set
```redis
hset event:judo availability:silver 2000
```

get all ket/value from matching pattern
```redis
hscan event:judo 0 match availability:*
```

add and delete a field
```redis
hset event:judo timezone JST
hget event:judo timezone

hdel event:judo timezone
```

delete hash set in 60 seconds
```redis
expire event:judo 60
```

check the remaining time
```redis
ttl event:judo
```
