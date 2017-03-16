## bochs-2.6.8 with redpill v0.1

### Platform
linux x86_64

### Download
```bash
git clone -b bochs-2.6.8-redpill --depth 1 https://github.com/mathfigure/bochs
```

### Build
```bash
cd bochs/bochs
./configure LIBS=-lrt
make
```

### Install
```bash
sudo make install
```

### Config (example)
```bash
$mkdir ~/vm1
$cp .bochsrc ~/vm1
$cd ~/vm1
# create a 400M hard disk image
$bximage -mode=create -hd=400M -q c.img
# change some things in the config file
$leafpad .bochsrc
cpu: model=pentium, ...
memory: guest=64, host=64
ata0-master: type=disk, path="c.img", mode=flat
ata0-slave: type=cdrom, path="win98.iso", status=inserted
boot: disk,cdrom
#sound: ...
```

### Run
```bash
bochs
```

### Test
```bash
# Note: The BOCHS_MEM includes RAM, ROM BIOS, ROM VGA, and some pad bytes
hexedit /dev/shm/BOCHS_MEM
```
