# vm-migration
resource-pool-vm-migration-lab/

├── README.md
├── commands/
│   └── validation_commands.sh
├── notes/
│   └── troubleshooting.md
└── screenshots/
    └── vm-in-resource-pool.png


==================== README.md ====================

# Resource Pool VM Migration Lab

## Overview
This project demonstrates creating a resource pool in VMware vSphere and migrating a virtual machine into it to manage CPU and memory allocation.

## Objective
Organize compute resources by placing a VM into a resource pool and validating system performance after migration.

## Technologies Used
- VMware vSphere
- Linux (RHEL/CentOS)
- Virtual Machines
- Resource Pools

## Setup Process

Create Resource Pool:
- Navigate to cluster
- Right-click → New Resource Pool
- Configure CPU and Memory settings

Migrate VM:
- Right-click VM (dev-app)
- Select Migrate
- Choose:
  Change compute resource only
- Select resource pool
- Finish migration

Modify Resource Pool (Optional):
- Right-click resource pool
- Edit Settings
- Adjust CPU/Memory limits and shares

## Verification

Check CPU:
lscpu

Check memory:
free -h

Monitor system:
top

Check processes:
ps aux | head

Verify network:
ip a
ping -c 4 8.8.8.8

Check services:
systemctl status httpd
curl localhost

Check disk:
df -h

## Outcome
VM successfully migrated into resource pool and remained operational with controlled resource allocation.

## Troubleshooting

- VM placed on host instead of pool
- Incorrect migration type selected
- Performance issues due to restrictive limits
- Verified placement through vSphere hierarchy

## Author
Farrell L. Shelton


==================== commands/validation_commands.sh ====================

#!/bin/bash

# Check CPU information
lscpu

# Check memory usage
free -h

# Monitor system performance
top

# List running processes
ps aux | head

# Check IP address
ip a

# Test internet connectivity
ping -c 4 8.8.8.8

# Check Apache service (if applicable)
systemctl status httpd

# Restart service if needed
systemctl restart httpd

# Test local service
curl localhost

# Check disk usage
df -h


==================== notes/troubleshooting.md ====================

# Troubleshooting Notes

## Issue: VM not in resource pool
Cause:
- Selected wrong destination during migration

Fix:
- Re-ran migration and selected correct resource pool

## Issue: Performance degradation
Cause:
- Resource pool limits too low

Fix:
- Adjusted CPU and Memory limits in resource pool settings

## Issue: VM placed on host instead of pool
Cause:
- Selected host instead of resource pool during migration

Fix:
- Verified hierarchy and re-migrated VM

## Issue: Services not responding
Cause:
- Resource constraints or service failure

Fix:
- Checked service:
  systemctl status httpd
- Restarted service:
  systemctl restart httpd

## Issue: Network connectivity issues
Cause:
- Misconfiguration or temporary failure

Fix:
- Verified IP:
  ip a
- Tested connectivity:
  ping -c 4 8.8.8.8


==================== GIT COMMANDS ====================

git init
git add .
git commit -m "Resource Pool VM Migration Lab with validation and troubleshooting"
git branch -M main
git remote add origin <your-repo-link>
git push -u origin main
