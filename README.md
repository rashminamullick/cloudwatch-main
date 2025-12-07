# cloudwatch-main
Document the step of cloudwatch 
📚 Table of Contents

Metric Selection

Alarm Conditions

Additional Configuration

SNS Topic Creation

Alarm Details

Testing with Stress Tool

Alarm Triggered

Metric Selection
I opened CloudWatch → Alarms → Create Alarm, and selected the metric for my EC2 instance.

I chose EC2 → Per-Instance Metrics to find the CPU metric for my instance.

I selected CPUUtilization for my app instance (i-095e1347ffe99ba5d). This tells CloudWatch what metric the alarm should watch.

alt text

Alarm Conditions
What I did next: I set the alarm to trigger when CPU usage Period: 10 seconds

alt text

is greater than 70%. alt text Datapoints to alarm: 2 out of 2

Missing data: Treat missing data as missing alt text

This means the alarm activates only if CPU stays high for two full periods.

Additional Configuration
Whatt I did next: For missing data, I kept the version shown in the picture — the default option. alt text

SNS Topic Creation
I created a new SNS topic so CloudWatch can email me when CPU goes above the threshold. alt text

Alarm Details
What I did: I added the alarm name and description explaining exactly what my alarm does. alt text

Testing with Stress Tool
What I did: I installed the stress tool using:

sudo apt install stress -y

I ran the stress tool using:

stress --cpu 2 --timeout 300

This forced my CPU to reach 100% so the alarm would trigger.

Alarm Triggered
alt text

After running the stress command, my alarm moved from OK → ALARM state. alt text This means the alarm works correctly
