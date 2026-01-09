# AWS Learning Journey
# Day 2 EC2 and EBS Deep Dive and Practice
#
# Topics Covered Today
#
# Topic 1 EC2 Compute Core (Practice)
# Topic 2 EBS Block Storage (Deep Dive and Practice)
#
# Topic 1 EC2 Compute Core Practice
#
# EC2 Stop vs Terminate Behavior
#
# When an EC2 instance is stopped:
# - CPU and RAM are released
# - Compute billing stops
# - Root and data EBS volumes remain intact
# - EBS storage cost continues
#
# When an EC2 instance is terminated:
# - Root EBS volume is deleted by default
# - Additional data EBS volumes remain unless explicitly deleted
# - This behavior is controlled by the “Delete on Termination” flag
#
# EC2 Performance Troubleshooting
#
# Observed scenario:
# - CPU usage low
# - RAM almost full
# - Disk I O spikes
#
# Root cause:
# - Memory bottleneck
# - Database cache exhaustion
# - Increased disk access due to cache misses
#
# Correct fix:
# - Upgrade EC2 instance size to increase RAM
# - Disk upgrade alone does not solve memory-bound issues
#
# High Availability Reality in EC2
#
# - A single EC2 instance is a single point of failure
# - AWS provides infrastructure reliability, not application HA
# - High availability must be designed by the user
#
# HA requires:
# - Multiple EC2 instances
# - Load balancer
# - Auto Scaling
# - Multi Availability Zone design
#
# Topic 2 EBS Block Storage Deep Dive
#
# What EBS Really Is
#
# - EBS is elastic block storage attached to EC2 over a storage network
# - Appears to the OS as a raw disk
# - Can be partitioned, formatted, and used for OS or data
# - Independent of EC2 lifecycle
# - Can be detached and attached to another EC2 instance
#
# AZ Scope vs Region Scope
#
# - EBS volumes are Availability Zone scoped
# - If an AZ fails, EBS volumes in that AZ become unavailable
# - EBS snapshots are region scoped
# - Snapshots remain available even during AZ failure
#
# IOPS vs Throughput
#
# - IOPS measures number of read and write operations per second
# - Throughput measures total data transferred per second
# - Databases are IOPS-bound due to many small random operations
# - Backups and file transfers are throughput-bound
#
# Key rule:
# - Databases fail due to IOPS limits
# - Backups fail due to throughput limits
#
# gp3 vs io2 Decision Logic
#
# gp3:
# - Cost effective
# - Flexible performance
# - Suitable for most workloads
# - Best-effort performance
#
# io2:
# - Expensive
# - Guaranteed IOPS
# - Predictable low latency
# - Used for mission-critical and latency-sensitive databases
#
# Best practice:
# - Start with gp3
# - Move to io2 only when guaranteed performance is required
#
# EC2 and EBS Performance Coupling
#
# - EBS performance depends on both volume type and EC2 instance limits
# - Upgrading gp3 to io2 does not help if EC2 EBS bandwidth limit is reached
# - Correct fix is to upgrade EC2 instance size
#
# EBS Snapshots
#
# - Snapshot is a point-in-time backup of an EBS volume
# - Snapshots are incremental
# - Only changed blocks are stored
# - Reduces storage cost and backup time
#
# Snapshots provide:
# - Disaster recovery
# - Volume restoration
# - Cross-AZ recovery
#
# Snapshots do NOT provide:
# - High availability
# - Live replication
#
# AZ Failure Recovery Using EBS
#
# If an Availability Zone fails:
# - EBS volumes in that AZ become unavailable
# - Snapshots remain available
#
# Fastest recovery:
# - Launch EC2 in another AZ
# - Create EBS volume from snapshot
# - Attach volume to EC2
# - Start application
#
# Practice Summary
#
# Practiced and validated:
# - EC2 stop and terminate behavior
# - Memory vs disk bottlenecks
# - EC2 and EBS performance limits
# - gp3 vs io2 selection
# - Snapshot-based disaster recovery
# - HA vs DR differences
#
# Key Takeaways
#
# - EC2 performance issues are often memory or instance-limit related
# - EBS is SAN-like storage, not local disk
# - Snapshots are for recovery, not high availability
# - High availability must be designed using live architecture
#
# Status
# Topic 1 EC2 Compute Core Practiced and Locked
# Topic 2 EBS Block Storage Practiced and Locked
