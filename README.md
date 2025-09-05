# config-center

English | [中文](README_zh.md)

## Design

### How to Reduce Redis Pressure

Use a sync-cache component to add an L1 local in-memory cache.

### Is Full Caching Required

Yes, it is necessary. During the startup phase of the L1 backend, a one-time MGET batch query can be used. This is highly worthwhile as it prevents subsequent, persistent, high-concurrency requests. Similarly, during the L2 Redis startup phase, configuration data can be fully cached to protect the database and prevent a large number of cache penetration requests after a Redis restart.

### Basic Deployment

Configure 2 pods and use maxSkew to ensure the pods are deployed on different nodes, avoiding a single point of failure while enabling horizontal scaling. Since the request volume is predictable, auto-scaling is not required; operations personnel can manually scale horizontally as needed.
