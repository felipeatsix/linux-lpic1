# 102 - Linux Installation and Packaging Management

## HD layout design

1. Find system partitions and their respective mount points
```
df -h
sudo fdisk -l
```

2. Find the size of swap area
```
cat /proc/swaps
free
top
```

4. Find the partition where the ESP is mounted
```
df /boot/efi
```

## Boot Manager (GRUB)

1. Identify the boot managegr in your system, and which GRUB version
```
ls /boot/grub:

menu.lst -> GRUB legacy
grub.cfg -> GRUB 2

ls /etc

lilo.conf -> LILO is installed instead GRUB
```

Another from of checking git is with command:
```
grub-install --version
```

2. Which Kernel version is being loaded by default by your boot loader?
This information can be found on the respective files depending on the boot manager:
```
/etc/lilo.conf
/boot/grb/menu.lst
/boot/grub/grub.cfg
```

## Shared libs management

7. Identify how many libs are mapped in your /etc/ld.so.cache ?
Execute the below command and read the first line:
```
ldconfig -p | less
```

8. Which external libs are used by the application "top"?
```
ldd /usr/bin/top | wc -l
```

## Debian Packages Management

1. Download the shell "ksh"
After running the below command, check the path `/var/cache/apt/archives/`
```
apt install -download-only ksh
```

2. Install ksh using "dpkg" and its dependencies
```
apt install --download-only binfmt-suppport
dpkg -i binfmt-support_2.1.6-1_amd64.deb
dpkg -i ksh_93u+20120801-2_amd64.deb
```

3. Install mysql-client
```
apt install mysql-client
```

4. Remove ksh completely (including configuration files)
```
apt purge ksh
```

5. Identify how many packages are installed on your system
```
dpkg --get-selections | wc -l
```

6. Identify the depedencies for the application `bash`
```
apt-cache depends bash
apt-cache show bash
dpkg -s bash
```

## Management of packages RPM & YUM

1. Download the package `nano`
```
yum install --downloadonly ---downloaddir=/tmp nano
```

2. Install nano
```
rpm -ivh nanoXXXXXXX.rpm
```

3. Check which version of nano was installed
```
rpm -qi nano
```

4. Remove nano using yum
```
yum erase nano
```

5. Update all packages of your distribution RedHat-based, without removing obsolete packages
```
yum update
```

6. Find the application related to the file /etc/sudoers
```
rpm -qf /etc/sudoers
```