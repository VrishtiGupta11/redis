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
