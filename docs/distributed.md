# MIT CS 6.824
Classic [Course](https://pdos.csail.mit.edu/6.824/) on distributed system
## concurrent primitive of golang
introduced [here](https://www.youtube.com/watch?v=UzzcUS2OHqo)

## lab
* the [labs](https://pdos.csail.mit.edu/6.824/schedule.html) explore MapReduce (distributed computing), Rafe (consensus algorithm), Raft/Sharded KV (distributed DataBase)
### lab1
* implement [mapreduce](https://pdos.csail.mit.edu/6.824/labs/lab-mr.html) framework, with one coordinator, and several workers to perform distributed computation
* remember to use `mu.Lock()`, `mu.UnLock()` for every handler of RPC to prevent race condition
* use go routine and function closure to set up timer, sending requests in parallel, etc to increase performance
```go
go func(){
    // wait for event
}()
```

### Lab 2
* [Raft](https://pdos.csail.mit.edu/6.824/papers/raft-extended.pdf) implementation consist of leader election, Log replication, Log Compaction, and persistance
#### lab 2A
* use `timer` to record election timeout, and heartbeat timeout
* parallelism on sending to all peers since they are independent

#### lab 2B
* thoroughtly understand what each field stands for make your life much easier
* several `replicators` goroutines that dedicate on retrying replication on each peer
* heartbeat also acts as a one time replicator.

