## Architecture Decisions

### Rust for the Tracking Service

- **Performance and Efficiency**: Rust is a systems programming language known for its focus on performance and efficiency. It provides fine-grained control over system resources, making it suitable for building high-performance applications like the tracking service that needs to handle a high throughput of requests (at least 500 req/s).

- **Concurrency and Scalability**: Rust's ownership model and built-in concurrency primitives allow for safe and efficient parallelism, enabling the tracking service to scale horizontally as the load increases.

- **Memory Safety**: Rust's strict memory safety guarantees minimize the risk of memory-related errors, making the tracking service more robust and less prone to crashes or security vulnerabilities.

### Kafka for the Pub/Sub System

- **Scalability**: Kafka is a distributed, horizontally scalable pub/sub messaging system that can handle high message throughput. It is designed for fault-tolerance and can be easily scaled by adding more brokers to the cluster, making it suitable for the requirements of the system.

- **Reliability and Fault Tolerance**: Kafka provides durable storage of messages and supports replication and fault tolerance. It ensures that messages are reliably delivered to consumers even in the presence of failures.

- **Data Streaming**: Kafka's ability to handle real-time streaming data makes it suitable for propagating events from the tracking service to the subscribed services efficiently.

### Golang for the CLI Client

- **Concurrency**: Golang (Go) is well-known for its excellent concurrency support, making it suitable for building concurrent and efficient CLI applications. The CLI client can efficiently handle multiple tasks, such as subscribing to the pub/sub system, filtering messages, and displaying results in real-time.

- **Fault Tolerance and Resilience**: Golang's built-in error handling and goroutines (lightweight threads) enable the CLI client to handle network errors seamlessly. It can recover from errors without requiring a full restart, ensuring a fault-tolerant behavior even in the presence of intermittent network connectivity issues.

- **Performance**: Golang's runtime is designed to be efficient, resulting in fast execution times. This is beneficial for a CLI client that needs to process and display messages in real-time, providing a responsive and performant user experience.


## Important note: 

Part of my technology/architecture decision was to learn rust, and to have fun :)

## Architecture overview
![image](https://github.com/SimeonAleksov/reimagined-octo-fortnight/assets/24735292/e2491ab8-916b-4365-b728-1f061bd1d6c0)

## Installing
To run this, first

```shell
$ cd tracking_service
$ docker compose up
```

After kafka, zoo, and postgres are up, we can run the go compose

```shell
$ cd cli
$ docker compose up
```

WIP!
- Clone the repository
```sh
git clone --recurse-submodules https://github.com/SimeonAleksov/reimagined-octo-fortnight
cd reimagined-octo-fortnight/
```


