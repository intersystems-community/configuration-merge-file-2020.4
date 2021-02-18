# Defining a Shard Architecture Topology

This CPF merge feature (see the two `.conf` files) shows how to implement an InterSystems IRIS shard architecture topology. The soloution has a series of **data nodes** that can grow horizontally. In this specifi example we have three fo them.

The first node of a shard cluster is always special and we call it the master node or  `NODE1` vs the remainders `DATA` nodes. However, you can leave it all to the system to figure it out and configure the cluster accodringly by using the `AUTO` option.

The shard node instances can be of type
- `NODE1` - that is the first shard node
- `DATA` - any subsequent data-shard instance that helps supporting the workload and scale horizontaly
- `COMPUTE` - for leveraging further computational power and buffers


The definition in the `.conf' files is very simple
- The *first* instance is defined as 
  - `ShardRole=auto`
- Subsequent shard *data* instances as
  - `ShardRole=auto`
  - `ShardClusterURL=IRIS://10.0.0.10:1972/IRISCLUSTER`
    - we basically decided at priori that the first serive is the first master node.

Please note how the sharding manager creates an *IRISCLUSTER* namespace that is avialable across the whole cluster for your use.

Figuratively we end up with the following architecture topology

``` 
NODE1 instance
        Sharded Namespace                        
                IRISCLUSTER

DATA  instance
        Sharded Namespace                        
                IRISCLUSTER
DATA  instance
        Sharded Namespace                        
                IRISCLUSTER
```

## Requirements
- a valid InterSystems IRIS shard-enabled key.
