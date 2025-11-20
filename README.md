# DevOps Intern Assignment

This repository contains my work for the DevOps Intern Assignment, where I deployed a monitoring setup on an EC2 instance, automated system reporting, and integrated the logs with AWS CloudWatch.

# Project Overview

The goal of this assignment was to launch an EC2 instance, configure a web server, generate periodic system reports using a Bash script, automate the script using cron, and send the logs to AWS CloudWatch for centralized monitoring.

# Tasks Completed
## 1. EC2 Setup

### Launched an Ubuntu EC2 instance in us-east-1 (N. Virginia).

### Connected to the instance using SSH.

### Installed and configured Nginx.

### Created a custom index.html displaying:
My name

Instance ID

Server uptime

# 2. System Monitoring Script

Created a Bash script at:

/usr/local/bin/system_report.sh


## This script collects:

### Current date and time

### System uptime

### CPU usage

### Memory usage

### Disk usage

### Top 3 CPU-consuming processes

The script outputs everything to:

/var/log/system_report.log

# 3. Cron Automation

Configured a cron job that runs the monitoring script every 5 minutes:

*/5 * * * * /usr/local/bin/system_report.sh >> /var/log/system_report.log 2>&1


This ensures reports are generated automatically without manual execution.

# 4. CloudWatch Integration

### Configured AWS CLI using a dedicated IAM user.

### Created a CloudWatch log group:
/devops/intern-metrics

### Created a log stream:
system-report-stream

### Generated a valid JSON log events file.

### Uploaded logs using:

aws logs put-log-events \
  --log-group-name "/devops/intern-metrics" \
  --log-stream-name "system-report-stream" \
  --log-events file:///tmp/log_events.json \
  --region us-east-1


Logs successfully appeared in CloudWatch.

# Technologies Used

### AWS EC2

### AWS CloudWatch

### IAM

### AWS CLI

### Bash scripting

### Cron

### Nginx

# Conclusion

This assignment helped me gain hands-on experience with EC2 setup, Linux automation, AWS CLI usage, CloudWatch log management, and creating automated monitoring solutions.
