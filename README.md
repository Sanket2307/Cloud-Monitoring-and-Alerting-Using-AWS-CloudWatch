# Cloud Monitoring and Alerting Using AWS CloudWatch

## Project Overview
This project implements a real-time cloud monitoring and alerting solution using AWS CloudWatch. The objective is to continuously monitor the performance of an EC2 instance and automatically notify administrators when system-defined thresholds are breached. The project demonstrates how cloud-native monitoring tools can proactively detect performance issues and improve system reliability.

The solution focuses on CPU utilization monitoring and email-based alerting using AWS managed services.

---

## Problem Statement
A standalone EC2 instance running an application may experience performance degradation during high load conditions. Without proper monitoring, such issues go unnoticed until system failure or service downtime occurs. Manual monitoring is inefficient and not scalable.

This project addresses the problem by implementing automated monitoring and alerting using AWS CloudWatch and SNS.

---

## Solution Overview
The EC2 instance is monitored using CloudWatch metrics. A CloudWatch alarm is configured to track CPU utilization. When the CPU usage exceeds a defined threshold (35%), the alarm changes its state to ALARM and triggers an Amazon SNS topic. SNS then sends an email notification to the administrator for immediate action.

This ensures proactive detection of performance issues and faster response times.

---

## AWS Services Used
- Amazon EC2 – Compute resource being monitored
- Amazon CloudWatch – Metric collection, visualization, and alarm configuration
- Amazon SNS – Notification service for sending alerts
- AWS IAM – Access control and permissions

---

## Architecture Explanation
1. An EC2 instance is launched with monitoring enabled.
2. Amazon CloudWatch continuously collects CPU utilization metrics from the EC2 instance.
3. A CloudWatch alarm is configured with a CPU utilization threshold of 35%.
4. When CPU usage exceeds the threshold for a defined evaluation period, the alarm transitions to the ALARM state.
5. The alarm triggers an Amazon SNS topic.
6. SNS sends an email notification to the subscribed administrator.

This architecture follows an event-driven and fully managed approach, eliminating the need for manual intervention.

---

## Monitoring and Alerting Workflow
1. Launch an EC2 instance
2. Enable detailed monitoring in CloudWatch
3. Create a CloudWatch alarm for CPU utilization
4. Configure threshold at 35%
5. Attach SNS topic to the alarm
6. Subscribe an email address to the SNS topic
7. Generate CPU load on the EC2 instance to test the alarm
8. Receive alert notification via email

---

## Alarm Configuration Details
- Metric: CPUUtilization
- Statistic: Average
- Threshold: Greater than 35%
- Evaluation Periods: 1
- Period: 5 minutes
- Action: Send notification to SNS topic

The threshold is intentionally set low for testing and demonstration purposes.

---

## Validation and Testing
To validate the monitoring and alerting mechanism, CPU stress is generated on the EC2 instance using a stress command. As CPU usage increases beyond the threshold, the CloudWatch alarm transitions to the ALARM state and an email notification is received via SNS.

This confirms the correctness of the monitoring pipeline.

---

## Recovery, RPO, and RTO
- Recovery Point Objective (RPO): Near real-time (metrics collected at minute-level granularity)
- Recovery Time Objective (RTO): Immediate notification upon threshold breach

The solution enables rapid awareness rather than automated recovery.

---

## Screenshots
The repository includes screenshots demonstrating:
- EC2 instance running state
- CloudWatch CPU utilization metrics
- Alarm configuration and threshold
- Alarm in ALARM state
- SNS email notification received

All screenshots are available in the `screenshots/` directory.

---

## Key Learnings
- Practical implementation of AWS CloudWatch monitoring
- Alarm creation and threshold tuning
- Integration of CloudWatch with SNS for automated alerts
- Understanding of proactive monitoring in cloud environments
- Hands-on experience with AWS IAM permissions

---

## Future Enhancements
- Add disk and memory utilization monitoring
- Integrate AWS Lambda for automated remediation
- Store logs using CloudWatch Logs
- Extend notifications to SMS or Slack
- Implement Auto Scaling based on alarm triggers

---

## Conclusion
This project demonstrates a foundational cloud monitoring and alerting system using AWS native services. It highlights the importance of observability, proactive alerting, and cloud automation in maintaining system reliability and performance.

