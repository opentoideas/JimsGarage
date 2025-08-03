1. Download the ISO using the GUI https://cloud-images.ubuntu.com/
2. tested
3. [https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64-disk-kvm.img](https://cloud-images.ubuntu.com/noble/current/noble-server-cloudimg-amd64.img)
1. Create the VM via CLI
```bash
qm create 5000 --memory 2048 --core 2 --name ubuntu-cloud --net0 virtio,bridge=vmbr0
cd /var/lib/vz/template/iso/
qm importdisk 5000 noble-server-cloudimg-amd64.img   local-zfs
qm set 5000 --scsihw virtio-scsi-pci --scsi0 local-zfs:vm-5000-disk-0
qm set 5000 --ide2 local-zfs:cloudinit
qm set 5000 --boot c --bootdisk scsi0
qm set 5000 --serial0 socket --vga serial0
```
3. Expand the VM disk size to a suitable size (suggested 10 GB)
```bash
qm disk resize 5000 scsi0 10G
```
4. change network to dhcp
5. Create the Cloud-Init template 
6. Deploy new VMs by cloning the template (full clone)

1. Download the ISO using the GUI https://cloud-images.ubuntu.com/
2. tested
3. [https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64-disk-kvm.img](https://cloud-images.ubuntu.com/noble/current/noble-server-cloudimg-amd64.img)
1. Create the VM via CLI
```bash
qm create 4000 --memory 2048 --core 2 --name ubuntu-cloud --net0 virtio,bridge=vmbr0
cd /var/lib/vz/template/iso/
qm importdisk 4000 jammy-server-cloudimg-amd64.img   local-zfs
qm set 4000 --scsihw virtio-scsi-pci --scsi0 local-zfs:vm-4000-disk-0
qm set 4000 --ide2 local-zfs:cloudinit
qm set 4000 --boot c --bootdisk scsi0
qm set 4000 --serial0 socket --vga serial0
```
3. Expand the VM disk size to a suitable size (suggested 10 GB)
```bash
qm disk resize 4000 scsi0 10G
```
4. change network to dhcp add ssh key
5. Create the Cloud-Init template 
6. Deploy new VMs by cloning the template (full clone)
