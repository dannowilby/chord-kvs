
# chord-kvs
An implementation of [this paper](https://pdos.csail.mit.edu/papers/chord:sigcomm01/chord_sigcomm.pdf). 

The project here is the result of the work of students @ UCSC: dwilby, anassadi, bgluu, and jkong--the different areas we worked on can be found in the contributions.yml.

# Features
- Sharding using consistent hashing
- Quorum-based replication
- Scalable Docker containers
- Causal/Eventual consistency
- Fault tolerant over network partitions and lost packets
- Robust gossip protocal

Currently, there is no way to detect if an individual replica is down.

# How to run
After cloning the repository, you will
1. Build the Docker image
2. Create a Docker subnet for the replicas
3. Run the number of replicas you want by creating that number of Docker container copies and specifying their ip/subnet
4. Send a `PUT` request to one of the containers with the following request body:
```
  num_shards: n, // an integer
  nodes: [] // the addresses of the other containers
```
Now you can send `PUT`, `GET`, and `DELETE` requests to any one of the containers to insert data efficiently and durably.

## Tests
After building the docker image
1. Run the `test.sh` file in the `tests` folder to set up the database
2. Run the `make_partition.sh` file to simulate network partitions using `iptables`
3. Run any of the `run_test_*.sh` scripts

# Status
This project is not currently being maintained.
