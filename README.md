# Redis

### Installation
https://redis.io/docs/getting-started/installation/install-redis-on-windows/

### About Redis
- In memory data structure store.
- Used as NoSQL database.
- Supports various data structures such as strings, hashes, list, sets, sorted sets, bitmaps, hyperloglog, geo-spatial indexes.
- Distributed cache.
- Message Broker (Software that enables applications, systems, and services to communicate with each other and exchange information.)

### Architecture
```
                       Sends and receives data
Redis Console Client <==========================> Redis Server
```
Here, both client and server can be same or different computers.

### Advantages
- It is fast as it uses primary memory for storing and accessing (1,10,000 writes per second | 81,000 reads per second).
- Persistent data.
- Support for data types.
- Atomicity i.e. if two different clients are concurrently accessing then redis will receive the updated values.
- Multi-Utility tool (used for caching | messaging queue as it supports Publish and Subscribe | short lived data in application such as storing web application sessions, page count hits, etc.)

| Commands | Output | Description |
|----------|--------|-------------|
| set name "Vrishti Gupta" | OK | |
| get name | "Vrishti Gupta" | |
| getrange name 0 8 | "Vrishti G" | |
| mset language English Technology Redis | OK | |
| mget language Technology | 1) "English" <br /> 2) "Redis" | |
| strlen language | (integer) 7 | |
| set counter 1 | OK | |
| get counter | "1" | |
| incr counter | (integer) 2 | |
| incrby counter 10 | (integer) 12 | |
| decr counter | (integer) 11 | |
| decrby counter 8 | (integer) 3 | |
| set pi 3.14 | OK | |
| get pi | "3.14" | |
| incrbyfloat pi 0.1 | "3.24" | | 
| expire pi 10 | (integer) 1 | It will expire the value of pi after 10 seconds |
| get pi | (nil) | Getting value of pi after 10 seconds |
| ttl pi | (integer) -2 | Time to live for pi after 10 seconds |
| setex var 30 "var_ttl = 30" | OK | To set expiry while setting the value |
| keys * | 1) "name" <br /> 2) "Technology" <br /> 3) "language" <br /> 4) "counter" | To show all the keys |
| flushdb ASYNC | OK | Deletes all keys from the connection's current database. |
| keys * | (empty array) | |
| flushall ASYNC | OK | Deletes all keys from all databases. |
