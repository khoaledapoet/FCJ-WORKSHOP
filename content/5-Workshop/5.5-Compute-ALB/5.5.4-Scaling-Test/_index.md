---
title: "Testing High Availability & Auto Scaling"
date: 2026-07-09
weight: 4
chapter: false
pre: " <b> 5.5.4. </b> "
---

To validate that our infrastructure dynamically scales under high traffic, we will simulate a CPU resource exhaustion event directly inside one of the active backend instances.

#### Step 1: Access the Backend EC2 Instance
Connect to any live EC2 instance spawned by the Auto Scaling Group (ASG) utilizing **AWS Systems Manager Session Manager** for secure, shell-free access.

#### Step 2: Install the `stress` Utility
Execute the following commands to install the stress testing utility on Amazon Linux 2023:

```bash
sudo apt update
sudo apt install -y stress
```

#### Step 3: Force 100% CPU Utilization
Execute the tool to heavily stress 2 CPU cores for 600 seconds (10 minutes):

```bash
stress --cpu 2 --timeout 600s
```
*(You can open another session and run the `top` utility to observe the CPU metric immediately spiking to 100%).*

#### Step 4: Verify the Scaling Behaviors on AWS Console
1. **CloudWatch Alarms:** Within 2-3 minutes, as aggregate telemetry surpasses 80%, the configured target alarm shifts from `OK` to **`In alarm`** state.
2. **Auto Scaling Actions:** Navigate to ASG > **Activity history**. You will observe an automated event triggered: *"Launching a new EC2 instance..."*. The ASG successfully provisions a new healthy node to handle the resource spike.
3. **System Cool-down:** Press `Ctrl + C` to terminate the `stress` process. Verify after the cooldown threshold that the ASG executes a **Scale-in** operation, safely terminating unnecessary instances to achieve cloud cost optimization.

![Auto Scaling Test Result](/images/asg-test-result.png)