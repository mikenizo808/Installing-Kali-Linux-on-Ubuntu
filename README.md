# Installing-Kali-Linux-on-Ubuntu

## Please Install `kvm` (or similar) First
This write-up assumes you can deploy a virtual machine on your system. For a refresher on getting your system ready, see the `kvm` section of my guide at:

    https://github.com/mikenizo808/Building-the-Ultimate-Ubuntu-Desktop-on-a-Pre-Made-Gaming-PC


## Download the bits
Visit the `kali.org` website and download the `Baremetal` version which will be an `.iso` that we can use later with the `Ubuntu` virtualization solution `kvm`.

## Checksum the bits
Optionally, use the `sha256sum` command to show the checksum of the downloaded iso file.

    sha256sum


## Example Output

    mike@ubuntu03:~$ sha256sum ./Downloads/kali-linux-2021.4a-installer-amd64.iso 
    31a21157378380e2c33b1cee39c303141b3f3c658fde457a545eb948094fab14  ./Downloads/kali-linux-2021.4a-installer-amd64.iso

## List Your Current ISOs
Your ISOs can be stored anywhere, but the official location is `/var/lib/libvirt/images/`. Use the `ls` command to list the directory contents.

    ls -lh /var/lib/libvirt/images/

## Copy an ISO (move tehchnically to save space)
Use `mv` to move the iso file to the desired location.

    #example
    sudo mv ./Downloads/kali-linux-2021.4a-installer-amd64.iso /var/lib/libvirt/images/

## Optional - List directory again

    sudo ls -lh /var/lib/libvirt/images/

## Example Output

    mike@ubuntu03:~$ sudo ls -lh /var/lib/libvirt/images/
    total 2.9G
    -rw-rw-r-- 1 mike mike 2.9G Jan  3 18:53 kali-linux-2021.4a-installer-amd64.iso
    mike@ubuntu03:~$ 

## Create the VM
Locate the `vmm` icon in your applications.  This is the `Virtual Machine Manager` that we installed earlier from the command line.  It gives us a nice GUI to create virtual machines, take snapshots, etc.  For now, we will just create the VM.

Click the `+` sign and choose `generic` for the operating system.  There is an autodetect feature, but it currently does not detect `kali` as the os.

Then click through to add the desired amount of cpu and memory.  On my desktop that has 16GB RAM and 16 Processors, I give my `kali` 4 vCPU and 8GB RAM.  This is totally up to you though since you can go light or heavy.

For disk, be sure to give enough space.  I go with 80 GB and also choose drive encryption.  I allow the system to choose auto lvm or similar and it does a good job of breaking things out like `/tmp`, etc. so you do not need to think about it.

Finally, power on the system and go through the guided install.  You will need to stay at the console for the entire install since you will get some prompts all the way to the end.

## Login to `kali`
With your VM powered on, click onto the screen so the console takes focus, then you can login with your user and password created earlier during setup.

*Tip: By default `kali` will make you type in the username and password, so be careful not to type your password into username field!*

## Update Kali
Launch a terminal and perform the following.

    sudo apt update
    sudo apt upgrade -y
    

## Summary
In this write-up, we got you up and running with `kali` Linux as a virtual machine on `Ubuntu`.
