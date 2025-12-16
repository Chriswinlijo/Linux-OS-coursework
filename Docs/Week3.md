Week 3- Select application for different workloads
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. Application Selection Matrix

| Workload Type | Application / Service | Why I chose it (justification) | What I will observe |
|---|---|---|---|
| CPU-intensive | `sysbench` (CPU test) | Produces repeatable CPU load (e.g., prime calculations) and is easy to run via SSH for consistent comparisons across runs. | CPU utilisation, load average, per-process CPU, execution time. |
| RAM-intensive | `stress-ng` (memory / vm workers) | Allows controlled memory pressure (allocation + page activity) to observe memory behaviour and potential swapping under load. | RAM usage, swap activity, system responsiveness, OOM risk signs. |
| I/O-intensive | `fio` | Industry-standard disk benchmark tool; can simulate random/sequential read/write with configurable block sizes to stress storage. | IOPS, throughput, latency, disk wait times, filesystem impact. |
| Network-intensive | `iperf3` | Simple, measurable throughput testing between workstation and server over the Host-Only network (safe lab traffic). | Throughput (Mb/s), packet loss signs, CPU cost of network traffic. |
| Server application | `nginx` (HTTP server) | Lightweight real server workload that supports response-time testing and concurrent requests without a GUI. | Response time, concurrent request handling, CPU/RAM impact while serving traffic. |

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2: Installation Documentation

| Task | Command(s) |
|---|---|
| Update package lists | sudo apt update |
| Install CPU & RAM stress tool (stress-ng) | sudo apt install stress-ng -y |
| Install CPU benchmarking tool (sysbench) | sudo apt install sysbench -y |
| Install disk benchmarking tool (fio) | sudo apt install fio -y |
| Install network performance tool (iperf3) | sudo apt install iperf3 -y |
| Install web server (nginx) | sudo apt install nginx -y |
| Start nginx service | sudo systemctl start nginx |
| Enable nginx on boot | sudo systemctl enable nginx |

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Expected Resource Profiles

| Application   | Expected CPU Usage                                         | Expected Memory Usage                                  | Expected Disk Usage                               | Expected Network Usage                                      |
| ------------- | ---------------------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------- | ----------------------------------------------------------- |
| **stress-ng** | Very high CPU when CPU workers are enabled (multi-core)    | Medium–high depending on the memory/vm options chosen  | Low                                                | Low                                                         |
| **fio**       | Low–moderate CPU (depends on I/O depth and job settings)   | Low                                                    | Very high disk activity (read/write throughput/IOPS) | Low                                                         |
| **iperf3**    | Low–moderate CPU at high throughput                        | Low                                                    | Minimal                                            | Very high throughput during tests                            |
| **nginx**     | Low at idle; increases with concurrent requests            | Low–medium (depends on connections and caching)        | Low (mainly logs)                                  | Medium–high depending on request rate and response size      |

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Week 3 — Part 4: Monitoring Strategy

### Server Performance Monitoring
- curl — check HTTP availability and measure response time for nginx
- ab (ApacheBench) — generate concurrent HTTP requests and record throughput/latency

### CPU & Memory Monitoring
- htop — interactive view of CPU, memory, and processes
- top — live system snapshot for CPU and RAM usage
- mpstat — per-core CPU utilisation statistics
- vmstat — system activity, run queue, and memory pressure indicators

### Network Monitoring
- iperf3 — measure bandwidth between the workstation and server (Host-Only link)
- ping — latency and connectivity checks
- ss -tulpn — confirm listening services and inspect active connections

### Disk I/O Monitoring
- iostat — observe disk utilisation, throughput, and I/O behaviour during tests
- df -h — check filesystem usage/capacity
- Compare disk behaviour before vs after fio workloads


