
Week 6 Overview: Performance Evaluation and Analysis
-----------------------------------------------------

In Week 6 I will run structured performance tests on my server to understand how the operating system behaves under different workloads. I will measure and compare key metrics (CPU, memory, disk I/O, network performance, system latency, and service response times), starting with a baseline when the system is idle and then repeating tests under load. I will use the results to identify bottlenecks and then apply optimisation changes, aiming to evidence at least two measurable improvements. For the journal and video, I will document my testing approach, record results in a performance data table, create charts/graphs, capture terminal evidence during tests, include a network latency/throughput analysis, and summarise optimisation outcomes with quantitative before/after results. 



All tasks were completed through SSH from my workstation to maintain headless administration.

---

## Testing Method (Workflow)
I followed a repeatable process:

1. Record baseline (idle)
2. Apply one workload at a time (CPU / memory / disk / network)
3. Monitor performance using CLI tools
4. Identify the main bottleneck(s)
5. Apply an optimisation
6. Re-test and compare before vs after

---

## Baseline Measurements (Idle)

### Commands Used
- `uptime` — shows system load averages
- `free -h` — shows RAM and swap usage
- `df -h /` — shows disk space usage for the root filesystem
- `iostat` — shows CPU and disk I/O activity

I will show below

<img width="851" height="187" alt="fe1575c8-31b2-4923-a9a9-e1aa94698c12_black_more_green" src="https://github.com/user-attachments/assets/d6e59e86-369f-45e0-91c0-db74ac887407" />

-------------------------

<img width="951" height="443" alt="1a5e3ef2-73c3-4639-b9de-6e31e624c0ce_black_more_green" src="https://github.com/user-attachments/assets/318e0182-351a-4f9d-a081-2263ef33b27f" />


Baseline results showed low load averages, high available memory, and minimal disk activity. 

------------------------------------------------------------------------------------------------

## CPU Performance Test

### Commands Used
- `stress-ng --cpu 2 --timeout 60 --metrics-brief`
- `uptime`
- `top`

### What These Commands Do
- `stress-ng --cpu` creates sustained CPU load using worker threads
- `uptime` shows how load averages change during CPU pressure
- `top` shows real-time CPU usage and active processes
- 
<img width="851" height="151" alt="ff8acd7e-1327-4b7e-9424-82ebaa140414_black_more_green" src="https://github.com/user-attachments/assets/de7e4ab3-d62c-403b-8c10-8da519c90df2" />

------------------------

<img width="883" height="63" alt="190a264a-76e2-4817-88cc-2c89e58f5512_black_more_green" src="https://github.com/user-attachments/assets/f1aacb9a-3a28-401e-baea-33fa007bbfa5" />

--------------------


<img width="657" height="41" alt="cd9f3508-3580-451a-9e7b-1f2a70d9fa99_black_more_green" src="https://github.com/user-attachments/assets/d0409801-9159-4d33-8eec-7519c650a843" />

-----------------------

<img width="1197" height="657" alt="77f15a37-7786-4c7b-94ab-24f4bf8864ff_black_more_green (1)" src="https://github.com/user-attachments/assets/605b6a12-7369-40a7-9b76-4456ee444cdd" />

----------------

Under CPU stress, load averages increased significantly compared to baseline. This indicates CPU saturation and shows how the scheduler handles a CPU-bound workload under sustained demand.

-------------------------------------------------------------------------------------------------
## Memory Performance Test

### Commands Used
- `stress-ng --vm 1 --vm-bytes 75% --timeout 60 --metrics-brief`
- `free -h`

### What These Commands Do
- `--vm` allocates memory to simulate pressure on RAM
- `--vm-bytes 75%` consumes most available memory
- `free -h` shows memory availability before/after the test

---------------------------------------------------

<img width="940" height="51" alt="284e6950-0f55-48de-893b-6fa61452e83a_black_more_green" src="https://github.com/user-attachments/assets/f1920b08-4b1b-4e61-9da3-f62c930bb7d6" />

----------------------------------------------------------------------------

<img width="817" height="118" alt="77c59558-aa41-4c51-874a-b7a552399893_black_more_green" src="https://github.com/user-attachments/assets/a9082130-e85f-40fe-ac65-57782f32f53f" />



Memory pressure reduced available RAM and increased memory utilisation. This demonstrates how Linux manages memory allocation under constrained conditions.

------------------------------------------------------------------------------------------------


### Optimisation Applied
I reduced swappiness to minimise unnecessary swapping and improve responsiveness under memory pressure.

### Commands Used
- `sudo sysctl vm.swappiness=10`
- `sudo nano /etc/sysctl.conf`
- `sysctl vm.swappiness`


<img width="655" height="86" alt="e4fa8a30-4feb-4677-9e60-284ddb59f52e_black_more_green" src="https://github.com/user-attachments/assets/7e67f992-6456-4d1c-b45a-10292f5aa6e5" />

---------------------------------------------------------------------------------------

<img width="1192" height="630" alt="week6_sysctl_conf_nano_black" src="https://github.com/user-attachments/assets/ab3e1b6e-7ada-4750-9be3-09dfe4e73339" />


<img width="655" height="86" alt="e4fa8a30-4feb-4677-9e60-284ddb59f52e_black_more_green" src="https://github.com/user-attachments/assets/54c63e1f-41c5-4384-bec7-7add275bec4b" />

still active

## Re-test After Optimisation (Memory)

### Commands Used
- `stress-ng --vm 1 --vm-bytes 75% --timeout 60 --metrics-brief`
- `free -h`

<img width="1200" height="102" alt="afb45755-49ec-4eff-82e9-d592696f463e_black_more_green" src="https://github.com/user-attachments/assets/e748a7bd-88cb-4bcb-acfe-6fe63f587a43" />

------------------------------------------------------------------------------------------------------------------------------------------------------


<img width="832" height="87" alt="73404de5-6b84-44f0-b741-ce59314a2c30_black_more_green" src="https://github.com/user-attachments/assets/80815321-3f54-4fe5-b817-2fb02eb0e015" />

------------------------------------------------------



