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

### Start the redis server
`sudo service redis-server start`

### Connect to redis-cli
redis-cli

### Key-value commands

<details>
<summary>Click to expand!</summary>

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

</details>

### List commands

<details>
<summary>Click to expand!</summary>

| Commands | Output | Description |
|----------|--------|-------------|
| lpush country India UK | (integer) 2 | |
| lrange country 0 -1 | 1) "UK" <br /> 2) "India" | |
| rpush country USA | (integer) 3 | |
| lrange country 0 -1 | 1) "UK" <br /> 2) "India" <br /> 3) "USA" | |
| llen country | (integer) 3 | |
| lset country 0 Russia | OK | |
| lrange country 0 -1 | 1) "Russia" <br /> 2) "India" <br /> 3) "USA" | |
| linsert country BEFORE USA UK | (integer) 4 | |
| lrange country 0 -1 | 1) "Russia" <br /> 2) "India" <br /> 3) "UK" <br /> 4) "USA" | |
| linsert country AFTER India Italy | (integer) 5 | |
| lrange country 0 -1 | 1) "Russia" <br /> 2) "India" <br /> 3) "Italy" <br /> 4) "UK" <br /> 5) "USA" | |
| lindex country 1 | "India" | |
| lpushx Movies "Harry Potter" "3 idiots" | (integer) 0 | Pushes the element, only if key (list) exists |
| sort country ALPHA | 1) "India" <br /> 2) "Italy" <br /> 3) "Russia" <br /> 4) "UK" <br /> 5) "USA" | |

</details>

### Set commands

<details>
<summary>Click to expand!</summary>

| Commands | Output | Description |
|----------|--------|-------------|
| sadd technology Java Redis React Flutter Angular MongoDB Firebase | (integer) 7 | To add elements in set |
| smembers technology | 1) "React" <br /> 2) "Java" <br /> 3) "Redis" <br /> 4) "MongoDB" <br /> 5) "Firebase" <br /> 6) "Flutter" <br /> 7) "Angular" | To get the elements of the set |
| scard technology | (integer) 7 | To get the count of the elements in the set |
| sismember technology Java | (integer) 1 | |
| sadd frontend React Angular HTML CSS | (integer) 4 | |
| sdiff technology frontend | 1) "Flutter" <br /> 2) "MongoDB" <br /> 3) "Redis" <br /> 4) "Firebase" <br /> 5) "Java" | Returns difference b/w sets i.e elements that are not available in 2nd set |
| sdiffstore diffSet technology frontend | (integer) 5 | To store the result in some other set |
| sinter technology frontend | 1) "Angular" <br /> 2) "React" | Returns the intersection of two sets |
|  sinterstore interSet technology frontend | (integer) 2 | To store the result of intersection in some other set |
| sunion technology frontend | 1) "Firebase" <br /> 2) "HTML" <br /> 3) "Flutter" <br /> 4) "Angular" <br /> 5) "Java" <br /> 6) "React" <br /> 7) "MongoDB" <br /> 8) "Redis" <br /> 9) "CSS" | |
| sunionstore unionSet technology frontend | (integer) 9 | |

</details>
