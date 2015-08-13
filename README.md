# VMware vSphere CLI

VMware vSphere CLI is a command-line tool to interact with VMware vSphere vCenter. The following are things it can do:

  - Power ON/OFF/RESET multiple VMs
  - Shutdown/Reboot/Suspend multiple VMs
  - Creating/Deleting/Reverting VM snapshots
  - Migrate one or more VMs
  - Check and upgrade VMware tools on multiple VMs
  - List all datacenters, clusters, hosts and datastores managed by the vCenter
  - ...

### Version
0.1

### Installation

You need to have pysphere 0.1.7 or higher installed:

```sh
# pip install pysphere
```
### Examples

To connect vmware tool to a vCenter

```sh
$ vscli -u parinya -s vcenter.home.lab
```

To list ALL VMs and templates

```sh
parinya@vcenter.home.lab> ls
```

To list ONLY powered-on VMs

```sh
parinya@vcenter.home.lab> ls -s on
```

Creating a snapshot on virtual machine vm1 vm2 vm3

```sh
parinya@vcenter.home.lab> mksnap -n snapshot1 -i "CHG0000001" vm1 vm2 vm3
```

Removing a snapshot "snapshot1" on virtual machine vm1 vm2 vm3

```sh
parinya@vcenter.home.lab> rmsnap -n snapshot1 vm1 vm2 vm3
```

Power-on virtual machine vm1 vm2 vm3

```sh
parinya@vcenter.home.lab> poweron vm1 vm2 vm3
```

To get all vm1 information

```sh
parinya@vcenter.home.lab> info vm1
```

To check how much memory has been allocated to vm1

```sh
parinya@vcenter.home.lab> get memory_mb vm1
```

To get vm1 and vm2 networking information

```sh
parinya@vcenter.home.lab> get net vm1 vm2
```

To migrate vm1 and vm2 to esx2.home.lab host

```sh
parinya@vcenter.home.lab> migrate -t esx2.home.lab vm1 vm2
```

Check VMware tools on vm1 and vm2

```sh
parinya@vcenter.home.lab> chktools vm1 vm2
```

Upgrade VMware tools on vm1 and vm2

```sh
parinya@vcenter.home.lab> uptools vm1 vm2
```

Access SHELL commands

```sh
parinya@vcenter.home.lab> !date
```

Getting help for the ls command

```sh
parinya@vcenter.home.lab> help ls
```

List all sub-commands available

```sh
parinya@vcenter.home.lab> help

Documented commands (type help <topic>):
========================================
EOF         exit  ls         lshost   mksnap    reboot  shutdown  uptools
chktools    get   lscluster  lsrp     poweroff  reset   standby
connect     help  lsdc       lssnap   poweron   rmsnap  status
disconnect  info  lsds       migrate  quit      rvsnap  suspend
```

### Config file

Filename .vscli.cfg

1. Look for .vscli.cfg in the current working directory
2. If 1.) cannot be found try .vscli.cfg in user HOME directory

NOTE: username and password via command line options overrides values in .vscli.cfg

Format:

```sh
[vcenter1_fqdn_in_lowercase]
username=user1
password=pass1

[vcenter2_fqdn_in_lowercase]
username=user2
password=pass2

....

```

### Todo's

 - Added new features (sub-commands)
 - Convert to use cmd2 module instead
 - Too many!!

License
----

GPLv2


### Links

[pysphere](https://code.google.com/p/pysphere/)



