
## Virtual Machines
<div style="text-align: justify;">
Virtual machines (VMs) are software-based emulations of physical computers that create isolated environments within a single physical host, enabling multiple operating systems to run concurrently on the same hardware. By leveraging virtualization technology, VMs abstract the underlying hardware, allowing each virtual instance—referred to as a guest—to operate independently with its own operating system and applications. This isolation enhances security, simplifies management, and optimizes resource utilization. Common use cases for virtual machines include software development and testing, where developers can quickly spin up and discard environments; server consolidation, which reduces the number of physical servers needed and lowers operational costs; and disaster recovery, by enabling easy backups and failovers. Additionally, VMs facilitate running legacy applications on modern hardware and support cloud computing infrastructures by providing scalable and flexible computing resources. Prominent hypervisors that manage and orchestrate virtual machines include VMware's ESXi, Oracle's VirtualBox, Microsoft's Hyper-V, and the open-source KVM (Kernel-based Virtual Machine). Core concepts behind virtual machines encompass the hypervisor layer, which can be either Type 1 (bare-metal) running directly on hardware or Type 2 (hosted) operating atop an existing operating system, as well as concepts like resource allocation, snapshotting, and live migration, which enhance the functionality and efficiency of virtualized environments. Together, these elements make virtual machines a foundational technology in modern IT infrastructure, enabling versatility and scalability across diverse computing needs. <nb>
For quick deployments, test and general purpose I use Virtualbox, for Production environments I go with Linux KVM solution and I manage my virtual machines through cockpit.
</div>

 `VBoxManage` and `qemu-img`, both of which are tools used for managing and converting virtual disk images between various formats.
### VBoxManage 
`VBoxManage` is the command-line interface for Oracle VM VirtualBox, allowing users to control all aspects of VirtualBox from the command line.
#### Converting Disk Images 
You can use `VBoxManage` to convert between different disk image formats such as `.vdi`, `.vmdk`, and `.raw`.**Examples:**  
1. **Convert VDI to VMDK:** 

```sh
VBoxManage clonehd source.vdi target.vmdk --format vmdk
```
 
2. **Convert VMDK to VDI:** 

```sh
VBoxManage clonehd source.vmdk target.vdi --format vdi
```
 
3. **Convert VDI to RAW:** 

```sh
VBoxManage clonehd source.vdi target.img --format raw
```

### qemu-img 
`qemu-img` is a versatile command-line utility that comes with QEMU, a generic and open-source machine emulator and virtualizer. It allows you to create, convert, and modify disk images.
#### Converting Disk Images 
You can use `qemu-img` to convert between various disk image formats including `.qcow2`, `.raw`, `.vmdk`, and `.vdi`.**Examples:**  
1. **Convert QCOW2 to RAW:** 

```sh
qemu-img convert -f qcow2 -O raw source.qcow2 target.img
```
 
2. **Convert VMDK to QCOW2:** 

```sh
qemu-img convert -f vmdk -O qcow2 source.vmdk target.qcow2
```
 
3. **Convert RAW to VDI:** 

```sh
qemu-img convert -f raw -O vdi source.img target.vdi
```
 
4. **Convert VDI to QCOW2:** 

```sh
qemu-img convert -f vdi -O qcow2 source.vdi target.qcow2
```

