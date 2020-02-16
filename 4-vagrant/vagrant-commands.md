# Useful commands to run Vagrant
These commands must be run in the terminal in order to control a Vagrant-generated Virtual Machine. These commands will allow us to launch, access (ssh), halt, check the status or remove from hard disk Virtual machines.

> Note: when any Vagrant command is run, Vagrant will look in the current directory fo any `Vagrantfile`. If it doesn't, it will keep on looking the upwards directories until the first `Vagrantfile` is found. The easiest way to run the correct `Vagrantfile` is to open the folder where the `Vagrantfile` can be found (check the current folder using the `pwd` command).

## 0 - Initializing Vagrant
```vagrant init```
- creates a 'default' `Vagrantfile` on the current folder, with has the minimum basic requirements to launch a VM.

## 1 - Launching the VM
```vagrant up```
- launches the virtual machine, with the specifications of the Vagrantfile since last time we ran `provision`. 

> Note: `vagrant up` will check if there is a Virtual Machine already built for that Vagrantfile (which means it is not the first time we run `vagrant up` in that folder). If there is, it simply launches it without looking at the `provision` statements of the `Vagrantfile` that download software packages such as `Python`. If there is no VM, `vagrant up` will launh the VM and run these `provision` statements.

```vagrant provision```
- checks the Vagrantfile, and downloads the required packages (if any is missing) to make the virtual machine work.


```vagrant reload --provision```
- restarts Vagrant VM with a new Vagrantfile configuration, provisioning all required packages (same as running `provision`). This command is useful to reload the VM after we modified the Vagrantfile.

## 2 - Connecting to the VM
```vagrant ssh```
- Vagrant accesses the initialized VM through SSH. After running this command, we 'enter' the VM and can pass commands to it. (To 'get out' of the VM, we can use the command `exit`; that will bring back the terminal to our local machine).

> Note: if we `exit` a running VM, it will not stop running, for that we need to **explicitely halt it** (see below).

## 3 - Halting the VM
```vagrant halt```
- stops the current vagrant VM running.

> Note: a specific VM can be halted by adding its unique id (a 7-digit Hex code such as `e3ea523`) using `vagrant halt <id-number>` (the `<id-number>` can be retrieved using [any of these commands](#4-checking-status)).


```vagrant suspend```
- suspends current VM running (same as 'hibernating': saves the current state of the machine)


```vagrant resume```
- resumes suspended VM

 # 4 - Checking status
```vagrant status```
- shows the status of the virtual machine on the current folder (tells us if it is running or not)


```vagrant gobal-status```
- shows the status of all created VMs in the machine

## 5 - Removing the VM from hard disk
```vagrant destroy```
- removes the VM from your hard disk
