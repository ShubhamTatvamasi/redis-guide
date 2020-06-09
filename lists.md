# lists

create a list, add all element to the left
```redis
lpush orders:4x100m-womens-final jane:4 bill:8 charlie:6
```

get the length of the list
```redis
llen orders:4x100m-womens-final
```

get all items from the list
```redis
lrange orders:4x100m-womens-final 0 -1
```

create a list, add all element to the right
```redis
rpush waitlist:basketball-mens-qual brain:2 kate:7 kevin:9
```

remove one item from right
```redis
rpop orders:4x100m-womens-final
```

remove one item from left
```redis
lpop waitlist:basketball-mens-qual
```

get item at index 1
```redis
lindex waitlist:basketball-mens-qual 1
```
