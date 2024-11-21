# CMPE283
Customized Linux kernel for KVM exit statistics tracking
CMPE – 283 VIRTUALIZATION
ASSIGNMENT 1 – VIRTUAL MACHINE / VMM SETUP

Student ID: 018184712
1.	Setting up Outer and Inner 
I have set up the Outer and Inner VM in the Assignment 1
2.	Fork and clone “Linux Kernel”
Repo Link: https://github.com/torvalds/linux

3.	Configured and Built the Kernel:
make menuconfig
make -j$(nproc)
make modules_install
make install

5.	Installed and Tested the Kernel:
sudo make install
sudo make modules_install
6.	Verified Kernel:
uname -r
7.	Located the Exit Handler Function
arch/x86/kvm/
8.	Added Print Statement:
if (global_exit_count % 10000 == 0) {
    printk("Exit Statistics:\n");
    for (int i = 0; i < NUM_EXIT_TYPES; i++) {
        if (exit_counts[i] > 0) {
            printk("Exit %d (%s): %lu\n", i, exit_name[i], exit_counts[i]);}
        } } 
9.	Built and Installed the Modified Kernel
make -j$(nproc)
sudo make install
sudo make modules_install
10.	Tested the Kernel with an Inner VM
Start the inner VM on the modified KVM.
Monitored VM Exists :  dmesg | grep "Exit Statistics"
11.	Commit and Submit
git add .
git commit -m "Added VM exit statistics to KVM"
git push origin main


THANK YOU
