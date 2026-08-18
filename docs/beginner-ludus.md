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

### Range Commands

For all `ludus range` commands, the flag `-r <range>` can be optionally used to specify a range. Otherwise, the default range is used (`ludus range default get`).

- `ludus range config get`

  Prints the current range configuration.

- `ludus range config set -f <file>`

  Updates the current range configuration.

  Note: Ludus copies the configuration file, so changes to the file specified will not be reflected in the configuration that Ludus is using.

- `ludus range deploy`

  Deploys the range. If the range is already deployed, this will rerun all of the stages, but does not rebuild the entire range from scratch. Most Ansible configurations are idempotent, so rerunning them is safe.

- `ludus range logs`

  Shows logs from the range deployment. This is extremely useful when debugging range config files. Use the `-f` flag to watch a live feed of the logs.

- `ludus range status`

  Provides information about the range, including name, id, deployment status, and VM info.

- `ludus range rm`

  Deletes all of the VMs associated with the range, but does not remove the range metadata (configuration, permissions, etc.). This is useful when you're low on resources. The range can be redeployed later, but any manual changes made after initial deployment will be lost.

- `ludus range rm-range`

  Deletes the range VMs and metadata. This entirely removes the range, so don't do this if you're going to reuse the range.

### Ansible Commands

- `ludus ansible role list`

  Lists the Ansible roles available on the Ludus host.

- `ludus ansible role add <rolename | roleurl | -d directory>`

  Adds an Ansible role to the Ludus host to be used in a range config file. The role can be imported from a galaxy.ansible.com, a URL, or a local file.
