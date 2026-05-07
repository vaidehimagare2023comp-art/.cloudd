11 // KVM
egrep -c '(vmx|svm)' /proc/cpuinfo
sudo apt update

together - sudo apt update
sudo apt install qemu-system-x86 libvirt-daemon-system libvirt-clients bridge-utils virt-manager -y

together-sudo systemctl enable libvirtd
sudo systemctl start libvirtd

sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
virsh list --all
kvm-ok
virt-manager


OR


Kernel-based Virtual Machine

KVM, an acronym for Kernel-based Virtual Machine, is an open source virtualization
technology integrated into the Linux kernel. It’s a type 1 (bare metal ) hypervisor that
enables the kernel to act as a bare-metal hypervisor.
KVM allows users to create and run multiple guest machines which can be either
Windows or Linux. Each guest machine runs independently of other virtual machines
and the underlying OS ( host system ) and has its own computing resources such as
CPU, RAM, network interfaces, and storage to mention a few.

1) Update Ubuntu 22.04

To get off the ground, launch the terminal and update your local package index as
follows.
$ sudo apt update
2) Check if Virtualization is enabled

Before you proceed any further, you need to check if your CPU supports KVM
virtualization. For this to be possible, your system needs to either have a VT-x( vmx )
Intel processor or an AMD-V (svm) processor.
This is achieved by running the following command. if the output is greater than 0, then
virtualization is enabled. Otherwise, virtualization is disabled and you need to enable it.
$ egrep -c &#39;(vmx|svm)&#39; /proc/cpuinfo

In addition, you can verify if KVM virtualization is enabled by running the following
command:
$ kvm-ok

Therefore, install the cpu-checker package as follows.
$ sudo apt install -y cpu-checker
Then run the kvm-ok command, and if KVM virtualization is enabled, you should get the
following output.
$ kvm-ok

3) Install KVM on Ubuntu 22.04
Next, run the command below to install KVM and additional virtualization packages on
Ubuntu 22.04.
$ sudo apt install -y qemu-kvm virt-manager libvirt-daemon-system
virtinst libvirt-clients bridge-utils
Let us break down the packages that we are installing:

● qemu-kvm – An open source emulator and virtualization package that
provides hardware emulation.
● virt-manager – A Qt-based graphical interface for managing virtual
machines via the libvirt daemon.
● libvirt-daemon-system – A package that provides configuration files required
to run the libvirt daemon.
● virtinst – A set of command-line utilities for provisioning and modifying
virtual machines.
● libvirt-clients – A set of client-side libraries and APIs for managing and
controlling virtual machines &amp; hypervisors from the command line.
● bridge-utils – A set of tools for creating and managing bridge devices.

4) Start &amp; Enable Virtualization Daemon

$ sudo systemctl enable --now libvirtd
$ sudo systemctl start libvirtd
Confirm that the virtualization daemon is running as shown.
$ sudo systemctl status libvirtd

5) Launch KVM Virtual Machines Manager
With KVM installed, you can begin creating your virtual machines using the virt-manager
GUI tool. To get started, use the GNOME search utility and search for ‘Virtual machine
Manager’.
