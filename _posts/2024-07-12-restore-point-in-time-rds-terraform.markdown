---
layout: post
title: "Restore RDS point in time using Terraform"
date: 2024-07-12 10:32:07 +1000
categories: til
tags: aws terraform rds
author: Eduardo Ramos
---

# Restore RDS point in time using Terraform

As part of our annual business continuity plan, we had to simulate a database less/corruption of our
main application, and steps to recover from backup.

Our application uses RDS instance, with continuous backup enabled. We can easily do it manually via AWS Web console
with a few clicks, but as the infrastructure is managed using Terraform, the best would be able to do the whole
operation using it. IaC laverages us to not just get infra running but also documented and reviewed later.

A simple search on DuckDuckGo for the terms `rds restore point in time terraform`, I got to the official documentation.

In short, I just had to provide the section `restore_to_point_in_time` containing 2 parameters:
* source_instance_identifier
* restore_time

The snippet was something like that:
```
module "db-restore" {
  source  = "terraform-aws-modules/rds/aws"
  version = "~> 3.0"

  identifier = "restored-instance"

 restore_to_point_in_time = {
   source_db_instance_identifier = "original-instance-identifier"
   restore_time                  = "2024-07-10T09:00:00+00:00"
 }

 ...
}
```

*Note that my environment is running on Terraform ~>3.0. Newer versions may provide different params
or different names for them.

References:
* [https://registry.terraform.io/modules/terraform-aws-modules/rds/aws/3.5.0#input_restore_to_point_in_time](https://registry.terraform.io/modules/terraform-aws-modules/rds/aws/3.5.0#input_restore_to_point_in_time)
* [https://medium.com/singapore-gds/performing-an-aurora-restore-to-point-in-time-with-terraform-3d5023d02937](https://medium.com/singapore-gds/performing-an-aurora-restore-to-point-in-time-with-terraform-3d5023d02937)
