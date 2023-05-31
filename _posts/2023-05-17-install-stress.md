---
title: Install stress on Amazon Linux 2023
date: 2023-05-17 12:00:00 +0800
categories: [Cloud, AWS]
tags: [cloud, aws, ec2, asg, devops]     # TAG names should always be lowercase
image:
  path: /assets/img/cli.jpg
---

# Install stress utility in Amazon Linux 2023

Install Stress Utility on Amazon Linux 2023
```shell
sudo yum install stress -y
```
Run 4 CPU stress
```shell
stress -c 4
```

AWS Auto Scaling is a service that helps you automatically scale your Amazon EC2 instances up or down based on demand. This can be a great way to ensure that you have enough resources to handle peak traffic, without overpaying for idle resources.

However, it's important to test your Auto Scaling group to make sure that it works as expected. One way to do this is to use the stress utility. The stress utility can be used to generate artificial load on your instances, which can help you test how your Auto Scaling group responds to increased demand.