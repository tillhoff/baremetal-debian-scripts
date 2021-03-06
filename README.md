# baremetal-debian-scripts

## what this is about

This contains my most used commands on new debian systems, so why not make it foolproof and create scripts for it?

## how to use

Install your Debian system.
If on Hyper-V, select the hyper-v network-driver.
At the end continue with only the 'basic-system-tools'-package selected.

```
$ su root # if needed
$ apt install -y git
$ exit
$ git clone https://github.com/thetillhoff/baremetal-debian-scripts
$ cd baremetal-debian-scripts
$ su root
$ ./initial.sh
## reboot
$ cd baremetal-debian-scripts
$ ./install-xrdp.sh
$ sudo ./install-docker.sh
## reboot (or poweroff on Hyper-V)
```

If you're running on Hyper-V also make sure the last poweroff/reboot is a poweroff, then close the vmconnect-window and reboot/-connect anew. Otherwise the enhanced session won't be available. Don't forget to run ```Set-VM -VMName <your_vm_name> -EnhancedSessionTransportType HvSocket``` on your Hyper-V host.


## remember
systemctl reboot/poweroff

## change bootorder from OS
If you have an EFI-based BIOS, you can change the boot-settings from your OS.
To display the current state run ```efibootmgr```.
To disable one of the entry run ```sudo efibootmgr -A -b 0008```.
```-A``` stands for disabling, while ```-a``` would stand for activating.
```-b XXXX``` contains the ID of the bootdevice.
