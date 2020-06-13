# Sets

add elements to a set
```redis
sadd venues "Olympic Stadium" "Nippon Budokan" "Tokyo Stadium"
```

get all the members in a set
```redis
sscan venues 0 match *
```

check if the member is part of a set
```redis
sismember venues "Nippon Budokan"
sismember venues "Eiffel Tower"
```

remove element from a set
```redis
srem venues "Nippon Budokan"
```

remove two random elements
```redis
spop venues 2
```
