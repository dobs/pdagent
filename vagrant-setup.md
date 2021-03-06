# Vagrant Setup

Vagrant setup notes for OS X 10.8 (Mountain Lion).

## Installation/Upgrade

1. Install Vagrant.  See instructions at http://www.vagrantup.com/

NOTE: If you experience issues in the 'Configuring and enabling network interfaces...' phase when bringing up centos instances, upgrade your vagrant to the latest.  My upgrade from v1.9.0 to v2.1.2 fixed this.

2. Install VirtualBox.  See instructions at https://www.virtualbox.org/

## Managing VMs

Run the command `vagrant status` in the project directory to list the VMs
defined in the project's `Vagrantfile`.

For example:

```
vagrant status
Current machine states:

agent-minimal-centos65    not created (virtualbox)
agent-minimal-centos72    not created (virtualbox)
agent-minimal-ubuntu1204  running (virtualbox)
agent-minimal-ubuntu1404  running (virtualbox)
agent-minimal-ubuntu1604  running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

You can bring up all VM at the same time by running `vagrant up` or bring up
an individual VM by specifying its name. For example:

`vagrant up agent-minimal-ubuntu1204`

**Note**: the first time that you bring up a VM may require a large download of the "box" that the VM is based on.  The box downloads will be cached in the
directory `~/.vagrant.d/boxes`.

You can manage the VMs using the Vagrant commands: `up`, `halt`, `reload`,
`suspend` and `resume`.

## Accessing the VM

You can ssh into a VM by using `vagrant ssh <machine-name>`. For example:

`vagrant ssh agent-minimal-ubuntu1204`

## Deleting VMs

You can delete Vagrant VMs by using the `vagrant destroy` command:

```
vagrant destroy
Are you sure you want to destroy the 'agent-minimal-ubuntu1204' VM? [y/N] y
[agent-minimal-ubuntu1204] Forcing shutdown of VM...
[agent-minimal-ubuntu1204] Destroying VM and associated drives...
```

## Vagrant cache

Vagrant caches VM downloads in `~/.vagrant.d/boxes`.  These are reused when you
destroy and rebuild a VM in the same project or in another project.  You may
want to check for and clean out old downloads here to recover disk space.
