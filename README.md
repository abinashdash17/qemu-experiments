# qemu-experiments
## How to boot qcow2 image with qemu
1. generate ssh key pair
2. edit the seed-iso-custom/user-data
3. paste the public key in the required line in the user-data file
4. generate seed.iso using the command : `genisoimage -output seed.iso -volid cidata -joliet -rock seed-iso-custom/`
5. use [virt-manager GUI](#How-to-install-using-virt-manager-GUI) or virt-install cli to install the qcow2 image
6. check the ip of the running vm using : `virsh net-dhcp-leases default`
7. login using : `ssh -i ssh_private.key username@ip_address`

## How to install using virt manager GUI
1. create a new VM
2. select the qcow2 image and choose correct operatign system name
3. specify ram and cpu core
4. check 'customize configuration before install'
5. select 'add hardware'
6. add storage
    1. device type: cdrom
    2. bus type: SCSI (very important, otherwise cloud-init might fail)
    3. select the 'seed.iso'
7. Begin Installation

## how to install using virt-install CLI
coming soon

## options for qcow2 or server os or cloud init
arch has a qcow2 image which comes with default user and pass arch:arch
all other cloud image comes without default username and pass and it must be initialized using cloud-init script or seed.iso

all cloud image user almost similar idle ram.
in ideal states the free ram would be around 200 to 300mb
the advantage of using arch image is that it has a default username and pass

## Sources
1. [Sample seed.iso](https://cdn.amazonlinux.com/os-images/2.0.20240809.0/)
2. A great intro to Qemu and CLI example: [QEMU: A proper guide!](https://www.youtube.com/watch?v=AAfFewePE7c)
3. A good tutorial for CLI without using seed.iso: [Qemu CLI setup guide](https://cloudinit.readthedocs.io/en/latest/tutorial/qemu.html)
4. Cloud init images for some popular linux Os
    1. [Debian Bookworm](https://cloud.debian.org/images/cloud/bookworm/20240717-1811/)
    2. [Arch](https://github.com/archlinux/arch-boxes) : I "used" Arch BTW!
        1. arch has a qcow2 image which comes with default user and pass arch:arch
    4. [Ubuntu](https://cloud-images.ubuntu.com/releases/24.04/release-20240809/) -
        1. (unrelated) it has ova images too, which can be used directly in Vitualbox.

### PS: 
I did some experiments with qemu. I have added all the steps here so that it might be helpful for others??? nah... it's for my future reference. haha...
