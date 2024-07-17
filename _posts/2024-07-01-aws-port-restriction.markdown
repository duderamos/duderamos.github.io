---
layout: post
title: "AWS port restriction"
date: 2024-07-01 14:26:07 +1000
categories: til
tags: aws
author: Eduardo Ramos
---
After a few hours trying to understand why my sidekiq job was failing to send out emails, getting
network time-out error, I finally found the reason.

It seems that for security reasons, which I agree partially, AWS blocks connections from ECS fargate containers to external services listening to TCP/25 (SMTP).

I could not find an official page/article to confirm this, the closest to it is [this one](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-resource-limits.html#port-25-throttle).
However, it is about EC2 and Lambda.

I did a test by changing my application to use the TCP/587 (submission) port, and happy days!
