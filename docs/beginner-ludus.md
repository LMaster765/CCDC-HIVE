# Beginner's Guide to Ludus

Ludus works by cloning VM *templates*, networking them together with a *Ludus configuration file*, and configuring them with *Ansible scripts*.

## Templates

Templates are the basic building block of ranges in Ludus. They are intended to be generic VM images that can be used to build networks. For example, a template would be a Debian 12 VM. Technically, you could create specialized templates (like a Debian 12 VM with a webserver hosted by nginx), but this specialization is supposed to be handled by Ansible.

## Ludus Range Configuration File

The Range Configuration File tells Ludus exactly how to build a range. This includes what templates should be used for each VM, disk and memory allocations, networking, device naming, and what Ansible roles should be applied.

You can see more info about the file specification on the [Ludus Docs](https://docs.ludus.cloud/docs/configuration/).

## Ansible Scripts

Ludus uses Ansible to specialize VMs after they are cloned and initialized based on the range configuration file. For more info on Ansible (since it is an entirely distinct system), check out the [Beginner's Guide to Ansible document](beginner-ansible.md).

## Useful Commands
