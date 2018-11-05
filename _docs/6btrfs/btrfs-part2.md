---
title: Btrfs перенос
category: Btrfs
order: 2
permalink:
post_video: 
post_photo_path: 
comments: true
edit: true
---

## Перенос снапшотов на раздел btrfs.
```bash
pacman -S rsync btrfs-progs arch-install-scripts
```

`lsblk` - подсветить все разделы что бы определиться что монтировать.

Монтируем.
```bash
mount /dev/sda6 /mnt
```

Создадим три подтома root, домашний каталог пользователя и подтом для хранения.
```bash
btrfs subvolume create /mnt/@_root
btrfs subvolume create /mnt/@_home
btrfs subvolume create /mnt/@_snapshots

btrfs subvolume list /mnt
```

Для переноса смонтируйте резервную систему и перенесите ее.
```bash
mkdir /mnt/dump
mount /dev/sdb1 /mnt/dump
```

```bash
rsync -aAXv --delete --delete-excluded --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","/var/lib/pacman/sync/*","/var/cache/*","/var/tmp/*","/boot/*","/home/*"} /mnt/dump/@/* /mnt/@_root/
```

```bash
rsync -aAXv --delete --delete-excluded --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","/var/lib/pacman/sync/*","/var/cache/*","/var/tmp/*","/boot/*","/home/*"} /mnt/dump/@home/* /mnt/@_home/
```

И отмонтируем корень ФС.
```bash
umount /mnt
rm -rf /mnt/dump
```

Чтобы монтировать подтом подобно обычному разделу диска, команде mount нужно указывать опцию subvol=PATH. PATH - путь относительно корня ФС. Монтируем корень.
```bash
mount -o subvol=@_root,compress=lzo,relatime,space_cache,autodefrag /dev/sda6 /mnt
```

What are the recommended options for installing on a pendrive, a SD card or a slow SSD drive? In `/etc/fstab` См. https://wiki.debian.org/Btrfs.

```bash
/dev/sdaX / btrfs x-systemd.device-timeout=0,noatime,compress=lzo,commit=0,ssd_spread,autodefrag 0 0
UUID=<the_device_uuid> /mount/point/ btrfs noauto,compress=lzo,noatime,autodefrag 0 0
```

Так же в параметрах указано сжатие lzo, что даёт прирост экономии места + повышает производительность, и дефрагметацию в фоне. Создаём папку и монтируем в неё наш будущий каталог пользователей. Если boot раздел отдеольно, нужно его тоже смонтироват в `/mnt/boot`.

Если нужно `mkdir /mnt/home`.
```bash
mount -o subvol=@_home,compress=lzo,relatime,space_cache,autodefrag /dev/sda6 /mnt/home
```

Если нужно `mkdir /mnt/snapshots`.
```bash
mount -o subvol=@_snapshots,compress=lzo,relatime,space_cache,autodefrag /dev/sda6 /mnt/snapshots

mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount -t sysfs none /mnt/sys

swapon /dev/sda2
```

Теперь нужно проинициализировать систему. Редактируем FSTAB, или запускаем genfstab.
```bash
rm /mnt/etc/fstab
genfstab -pU /mnt > /mnt/etc/fstab
```

Переходим в нашу новую систему.
```bash
arch-chroot /mnt /bin/zsh
```
Или Debian подобных.
```bash
chroot /mnt /bin/bash
pacman -Syy
```

Перегенерироваь файловую систему с помощью mkinicpio.
```bash
mkinitcpio -p linux
```

Установить загрузчик GRUB2 и сконфигурировать его.
```bash
grub-install /dev/sdХ
grub-mkconfig -o /boot/grub/grub.cfg
```

`exit` или "Ctrl + D" выйти из chroot.

Теперь  нужно все размонтировать.
```bash
umount /mnt/home
umount /mnt/snapshots
umount /mnt
reeboot
```

---