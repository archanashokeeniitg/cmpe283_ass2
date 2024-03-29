# CMPE283 Ass 2

Archana Shokeen(015237378) 

## Question
Your assignment is to modify the CPUID emulation code in KVM to report back additional information 
when special CPUID leaf nodes are requested.
•For CPUID leaf node %eax=0x4FFFFFFF:
◦Return the total number of exits (all types) in %eax
•For CPUID leaf node %eax=0x4FFFFFFE:
◦Return the high 32 bits of the total time spent processing all exits in %ebx
◦Return the low 32 bits of the total time spent processing all exits in %ecx
▪%ebx and %ecx return values are measured in processor cycles, across all VCPUs
•For CPUID leaf node %eax=0x4FFFFFFD:
◦Return the number of exits for the exit number provided (on input) in %ecx
▪This value should be returned in %eax 
•For CPUID leaf node %eax=0x4FFFFFFC:
◦Return the time spent processing the exit number provided (on input) in %ecx
▪Return the high 32 bits of the total time spent for that exit in %ebx
▪Return the low 32 bits of the total time spent for that exit in %ecx

# Steps

Initializing

Fork linux git repo https://github.com/torvalds/linux.git . and mine https://github.com/archanashokeeniitg/cmpe283-virtualtech.git

Building the Kernel

a. Enter root user mode with the following command:

`sudo bash`

b. Install kernel-package:


`apt-get install build-essential kernel-package fakeroot libncurses5-dev libssl-dev ccache bison flex libelf-dev `


c. Note down Kernel Version after the command:

`uname -r`


d. Substitute version obtained in Step c(previous step) into the following command:
`cp /boot/config-$(uname -r) ./.config` Replace (uname -r) eg- `cp /boot/config-5.8.0-50-generic ./.config`


e.Use the default for everything, Hold down enter for default settings while running the command:


`sudo make oldconfig`

f. Make

`sudo make -j`

sudo make modules && sudo make install && sudo make modules install

g. Reboot

`sudo reboot`

Verify newer kernel after reboot using:

`uname -a`

# Answers

## For assignment 2, select two of the four above CPUID leaf nodes and implement the functionality 
described, and answer the questions below.

Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there 
more exits performed during certain VM operations? Approximately how many exits does a full VM 
boot entail? Of the exit types defined in the SDM, which are the most frequent? Least?


No, the number of exits do not increase at a stable rate.

Yes, There are more exits performing during certain VM operations. A full VM boot entail around ~830000 exits.


