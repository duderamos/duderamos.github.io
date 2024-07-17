---
layout: post
title: "ECS Fargate and containers with init process"
date: 2024-07-11 10:32:07 +1000
categories: til
tags: aws docker containers
author: Eduardo Ramos
---
For a few weeks my team has noticed that our load balancer is reporting a spike of 5XX errors whenever we roll deployments.
There is actually no issue with the applications, and from user of our application perspective, everything goes well.
However, it stains our logs and reports.

After some research, we found that probably our application is taking a little longer to gracefully terminate, then Fargate
is sending SIGKILL to the container, causing a sudden disconnection between the container and load balance target.

In order to address this, we enabled our containers to run the application by a Linux init process, that will take care
of the process lifecycle and do the proper clean up of child processes.

It was the solution for the 5XX issues.

Reference:
* [https://aws.amazon.com/blogs/containers/graceful-shutdowns-with-ecs/](https://aws.amazon.com/blogs/containers/graceful-shutdowns-with-ecs/)
