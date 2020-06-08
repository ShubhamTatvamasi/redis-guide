# string

create a key/value pair
```redis
set inventory:4x100m-womens-final 1000
get inventory:4x100m-womens-final
```

decrement by 1
```redis
decrby inventory:4x100m-womens-final 1
get inventory:4x100m-womens-final
```

check the type of value
```redis
type inventory:4x100m-womens-final
```

check the encoding type of value
```redis
object encoding inventory:4x100m-womens-final
```

updating the value from int to string
```redis
set inventory:4x100m-womens-final "Sold out"
object encoding inventory:4x100m-womens-final
```

update the value back to int
```redis
set inventory:4x100m-womens-final 0
get inventory:4x100m-womens-final
```
