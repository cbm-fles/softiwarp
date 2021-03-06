#SoftiWARP

SoftiWARP (siw) is a software iWARP kernel driver and user library 
for Linux. It implements the iWARP protocol suite (MPA/DDP/RDMAP,
IETF-RFC 5044/5041/5040) completely in software, without requiring
any dedicated RDMA hardware. It comprises a loadable Linux kernel
module `siw` located in `kernel/` and a user level library `libsiw`
located in `userlib/`.


SoftiWarp targets for integration with the OpenFabrics (OFA)
ecosystem. For OFA integration, it is written against its kernel
and user level interfaces.

SoftiWARP supports both user level and kernel level applications.
It makes use of the OFA connection manager to set up connections.
The kernel component runs on top of TCP kernel sockets.

## Code structure
```bash 
kernel/:	kernel module
userlib/:	user library
common/:	common include file(s)
```

## Build and install 

### User-space library
 
```bash
 cd /path/to/your/clone/userlib
 ./autogen.sh
 ./configure
 make install
```
 
### Kernel module
 To build:
```bash 
cd /path/to/your/clone/kernel
make
```

To load:

settings 1: for binding TX thread to one arbitrary CPU 
(check dmesg which CPU runs TX thread) 
```bash
sudo insmod ./siw.ko
```

setting 2: for starting TX thread on all CPUs given in 
comma separated list, if CPU available
```bash
sudo insmod ./siw.ko tx_cpu_list=[n,m,...]
```

## Contributions

PRs are always welcome. Please fork, and make necessary modifications 
you propose, and let us know. 

## Contact 

If you have questions or suggestions, feel free to post at:

https://groups.google.com/forum/#!forum/zrlio-users

or email: zrlio-users@googlegroups.com

