---
layout: post
title: "Efficient storage usage with QCow2 images"
date: 2024-07-27 19:59:35 +1000
categories: til
tags: til qemu kvm
author: Eduardo Ramos
---
I have been away from sysadmin duties for a few years, and I missed it.
Today I decided to play a little bit with virtual machines in my Linux laptop, instead of installing a fresh Ubuntu server from an ISO image,
I looked for a pre-installed image compatible with QEMU/KVM stack, and happily, Ubuntu provides some.

Once downloaded, I thought, "what if I want to spin other VMs later? I don't want to modify this image now and have to download a new file again".
Then I remembered I got the same question before, and in the past, I found a way to create new images from a "base image".
The concept is similar to working with snapshots, only the new and modified bytes will be written on the disk through the technique called [copy-on-write](https://en.wikipedia.org/wiki/Copy-on-write)

This may sound complicated, but it can be achieved with a simple command:

`qemu-img create -f qcow2 -F qcow2 -b original_image_file.img new_image_file.img`

Note that the image I am using has the `qcow2` format, which is copy-on-write compatible. Find more information [here](https://github.com/qemu/qemu/blob/master/docs/interop/qcow2.txt).

Reference:
* [QEMU disk image utility](https://www.qemu.org/docs/master/tools/qemu-img.html#cmdoption-qemu-img-arg-create)
