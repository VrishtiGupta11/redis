# Redis

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

### Installation
https://redis.io/docs/getting-started/installation/install-redis-on-windows/

### Start the redis server
`sudo service redis-server start`

### Connect to redis-cli
`redis-cli`

### String commands

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

### Sorted set commands

<details>
<summary>Click to expand!</summary>

| Commands | Output | Description |
|----------|--------|-------------|
| zadd users 110 Vrishti 22 Hermione 44 Harry 35 John 20 Alexa | (integer) 5 | To add elements in sorted set along with their score |
| zrange users 0 -1 | 1) "Alexa" <br /> 2) "Hermione" <br /> 3) "John" <br /> 4) "Harry" <br /> 5) "Vrishti" | |
| zrange users 0 -1 withscores | 1) "Alexa" <br />  2) "20" <br />  3) "Hermione" <br />  4) "22" <br />  5) "John" <br />  6) "35" <br />  7) "Harry" <br />  8) "44" <br />  9) "Vrishti" <br /> 10) "110" | To get all the elements in sorted aet along with their scores. |
| zcard users | (integer) 5 | To get the count of number of elements in sorted set |
| zcount users 10 40 | (integer) 3 | To get the count of number of elements within the given range according to the score |
| zcount users -inf +inf | (integer) 5 | |
| zrem users Alexa | (integer) 1 | To remove any element from sorted set |
| zrange users 0 -1 rev withscores <br /> or <br /> zrevrange users 0 -1 withscores | 1) "Vrishti" <br /> 2) "110" <br /> 3) "Harry" <br /> 4) "44" <br /> 5) "John" <br /> 6) "35" <br /> 7) "Hermione" <br /> 8) "22"
| zscore users Vrishti | "110" | To get the zscore of any element |
| zrange users 40 10 byscore rev withscores <br /> or <br /> zrevrangebyscore users 40 10 withscores | 1) "John" <br /> 2) "35" <br /> 3) "Hermione" <br /> 4) "22" | |
| zincrby users 20 Hermione | "42" | To increment the score of any element |
| zremrangebyscore users 0 20 | (integer) 0 | To remove elements within the given range according to the score |
| zremrangebyrank users 0 1 | (integer) 2 | To remove elements within the given range according to the rank |

</details>

### Hyperloglog commands

<details>
<summary>Click to expand!</summary>

| Commands | Output | Description |
|----------|--------|-------------|
| pfadd hll a b c d e f g | (integer) 1 | add elements in hyperloglog |
| pfcount hll | (integer) 7 | |
| pfadd hll2 1 2 3 4 5 6 7 | (integer) 1 | |
| pfcount hll2 | (integer) 7 | |
| pfmerge mergedhll hll hll2 | OK | |
| pfcount mergedhll | (integer) 14 | |

</details>

### Hash commands

<details>
<summary>Click to expand!</summary>

| Commands | Output | Description |
|----------|--------|-------------|
| hset mp name Vrishti Phone 0123456789 age 18 <br /> or <br /> hmset mp name Vrishti Phone 0123456789 age 18 | (integer) 3 | |
| hkeys mp | 1) "name" <br /> 2) "Phone" <br /> 3) "age" | |
| hvals mp | 1) "Vrishti" <br /> 2) "0123456789" <br /> 3) "18" | |
| hgetall mp | 1) "name" <br /> 2) "Vrishti" <br /> 3) "Phone" <br /> 4) "0123456789" <br /> 5) "age" <br /> 6) "18" | |
| hexists mp name | (integer) 1 | |
| hlen mp | (integer) 3 | |
| hmget mp name Phone | 1) "Vrishti" <br /> 2) "0123456789" | |
| hincrby mp age 2 | (integer) 20 | |
| hincrbyfloat mp age 1.1 | "21.1" | |
| hdel mp Phone | (integer) 1 | |
| hstrlen mp name | (integer) 7 | |
| hsetnx mp name VG | (integer) 0 | To set the key value pair if it doesn't exist |

</details>
