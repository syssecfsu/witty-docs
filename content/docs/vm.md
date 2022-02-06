---
title: VirtualBox
weight: 5
---

## Use WiTTY with SEED VM

The [SEED labs](https://seedsecuritylabs.org/Labs_20.04/) provides a number of security hands-on labs. It is a popular security lab course taught at many universities. The SEED labs use [VirtualBox](https://www.virtualbox.org/) to run its VMs (because VirtualBox is cross-platform.) 

By default, the SEED VM uses only NAT-based network, which means that the VM can access the Internet but not the host machine (i.e., the machine that runs VirtualBox is called the host, and the VM is often called the guest.) We need to add a second, host-only network adaptor in order to run WiTTY in the guest and access WiTTY from a browser in the host. 

To do that, first open the `Host Network Manager` and create a host network if there is not one already, as shown below (on macOS):
![img](/static/img/host.png)

Then, open the setting for the SEED VM, go to the Network setting, and enable the second adaptor, choose the `host-only` adaptor. Leave the first adaptor as is. 

![img](/static/img/adapter2.png)

After this, start the VM and list all the adaptors using the command `ifconfig` in a terminal. Look for the adaptor with an IP address starting with `192.168.`. You should be able to ssh into the guest using this IP address from the host.