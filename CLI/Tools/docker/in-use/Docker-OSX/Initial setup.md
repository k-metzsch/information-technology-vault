
[Docker-OSX](https://github.com/sickcodes/Docker-OSX)

Before you do anything else, you will need to turn on hardware virtualization in your BIOS. 

Then, you'll need QEMU and some other dependencies on your host:

```bash
sudo pacman -S qemu libvirt dnsmasq virt-manager bridge-utils flex bison iptables-nft edk2-ovmf
```
