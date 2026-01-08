Topic 1 EC2 Compute Core
What I Learned
What EC2 Really Is

EC2 provides virtual servers created from powerful physical machines in AWS data centers.
AWS manages hardware and infrastructure, but high availability is the user’s responsibility.
A single EC2 instance is not highly available by default.

Instance Types Core Concept

Instance type is not just instance sizing.
It is a hardware profile defining:

CPU capability

RAM capacity

Network bandwidth

Storage throughput limits

Instance types must be chosen based on workload behavior, not cost alone.

Examples:

General purpose for small applications and web servers

Memory optimized for databases

Compute optimized for CPU intensive workloads

vCPU vs Physical Core

AWS uses hyper threading.
One physical CPU core equals two vCPUs.
vCPU represents a CPU thread, not a full physical core.
Some workloads such as databases and licensed software require dedicated physical cores.

Memory Is the Most Common Bottleneck

Most applications, especially databases, are memory bound.
RAM is much faster than disk, even SSD.

When RAM becomes full:

Cache misses increase

Disk I O spikes

Application slows down even if CPU usage is low

Upgrading disk does not fix memory problems.
Instance size must be increased.

Databases on EC2

Databases prefer:

High RAM

Predictable performance

Reduced disk access

Best practice:

Use memory optimized instances

Size based on RAM first, not CPU or disk

Performance Troubleshooting

Learned to diagnose:

Low CPU but slow application

Disk I O spikes during peak load

Performance degradation over time

Common root causes:

Memory exhaustion

Cache thrashing

Instance bandwidth limits

CPU credit exhaustion in burstable instances

High Availability Reality

A single EC2 instance is a single point of failure.
AWS provides infrastructure reliability, not application level high availability.

Users must design high availability using:

Multiple EC2 instances

Load balancers

Auto Scaling

Multi Availability Zone architecture

Practice Completed

EC2 performance troubleshooting scenarios

Database instance selection

Memory versus disk bottleneck analysis

Interview level EC2 questions

Outcome

After completing this topic, I can:

Select EC2 instance types correctly

Identify and fix EC2 performance issues

Explain EC2 internals in simple terms

Answer real world and interview level EC2 questions confidently


Snapshots

Database disk design
