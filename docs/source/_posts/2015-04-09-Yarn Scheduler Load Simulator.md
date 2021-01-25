---
layout: post
title:  "Yarn Scheduler Load Simulator (SLS)"
date:   2015-04-09 21:42:08
categories: jekyll update
---


### Yarn Scheduler Load Simulator (SLS) ####

[Yarn Scheduler Load Simulator (SLS)](https://hadoop.apache.org/docs/r2.4.0/hadoop-sls/SchedulerLoadSimulator.html#Step_1:_Configure_Hadoop_and_the_simulator)

The Yarn Scheduler Load Simulator (SLS) is such a tool, which can simulate large-scale Yarn clusters and application loads in a single machine.This simulator would be invaluable in furthering Yarn by providing a tool for researchers and developers to prototype new scheduler features and predict their behavior and performance with reasonable amount of confidence, thereby aiding rapid innovation.

The simulator will exercise the real Yarn ResourceManager removing the network factor by simulating NodeManagers and ApplicationMasters via handling and dispatching NM/AMs heartbeat events from within the same JVM. To keep tracking of scheduler behavior and performance, a scheduler wrapper will wrap the real scheduler.

The size of the cluster and the application load can be loaded from configuration files, which are generated from job history files directly by adopting Apache Rumen.

The simulator will produce real time metrics while executing, including:

Resource usages for whole cluster and each queue, which can be utilized to configure cluster and queue's capacity.
The detailed application execution trace (recorded in relation to simulated time), which can be analyzed to understand/validate the scheduler behavior (individual jobs turn around time, throughput, fairness, capacity guarantee, etc.).
Several key metrics of scheduler algorithm, such as time cost of each scheduler operation (allocate, handle, etc.), which can be utilized by Hadoop developers to find the code spots and scalability limits.
Goals

Exercise the scheduler at scale without a real cluster using real job traces.
Being able to simulate real workloads.
**Architecture**

The following figure illustrates the implementation architecture of the simulator.

![The architecture of the simulator](/images/sls_arch.png)

**The architecture of the simulator**
The simulator takes input of workload traces, and fetches the cluster and applications information. For each NM and AM, the simulator builds a simulator to simulate their running. All NM/AM simulators run in a thread pool. The simulator reuses Yarn Resource Manager, and builds a wrapper out of the scheduler. The Scheduler Wrapper can track the scheduler behaviors and generates several logs, which are the outputs of the simulator and can be further analyzed.