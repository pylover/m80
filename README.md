
SOC: Mediatek M80
Module: FM350-GL


uname: Linux expertbook 5.15.0-1016-intel-iotg #21-Ubuntu SMP Wed Sep 14 04:18:11 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

## Prerequicites

```bash
sudo apt-get -y install \
  build-essential \
  bc \
  bison \
  flex \
  libssl-dev \
  libncurses5-dev \
  libelf-dev \
  dwarves \
  zstd
```


## Fetch
```bash
git clone https://git.launchpad.net/~canonical-kernel/ubuntu/+source/linux-intel-iotg/+git/jammy/
cd jammy
```


## Configure
```bash
git reset --hard Ubuntu-intel-iotg-5.15.0-1016.21
cp /boot/config-$(uname -r) ./.config
make olddefconfig
scripts/config --set-str SYSTEM_TRUSTED_KEYS ""
scripts/config --set-str CONFIG_SYSTEM_REVOCATION_KEYS ""
scripts/config --enable WWAN
scripts/config --module CONFIG_MTK_T7XX
```

## Build
```bash
make -j8
rm scripts/gdb/vmlinux-gdb.py 
make deb-pkg
```

https://9to5linux.com/how-to-install-linux-kernel-6-0-on-ubuntu-22-10


https://gitlab.freedesktop.org/mobile-broadband
https://elixir.bootlin.com/linux/latest/source/include/linux/iopoll.h#L36
https://cateee.net/lkddb/web-lkddb/MTK_T7XX.html
https://www.intel.com/content/www/us/en/develop/documentation/ei4amr-2022-3-developer-guide/top/tutorials-amr/5g-modem.html
https://manpages.ubuntu.com/manpages/jammy/man1/wwan.1.html
https://lwn.net/Articles/890750/
https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg488798.html
https://ubuntu.com/core/docs/networkmanager/configure-cellular-connections


# Bugs
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1990700
https://lists.ubuntu.com/archives/kernel-team/2022-November/134458.html
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002089
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1950282


Listing...
linux-image-5.15.0-1016-intel-iotg/jammy-updates,jammy-security,now 5.15.0-1016.21 amd64 [installed,automatic]
linux-image-5.15.0-1023-intel-iotg/jammy-updates,jammy-security,now 5.15.0-1023.28 amd64 [installed,automatic]
linux-image-intel-iotg/jammy-updates,jammy-security,now 5.15.0.1023.22 amd64 [installed,automatic]

