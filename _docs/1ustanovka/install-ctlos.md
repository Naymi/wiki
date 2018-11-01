---
title: Установка Ctlos
category: Установка
order: 1
post_video: 
post_photo_path: 
comments: true
edit: true

---
Скачайте образ: [https://ctlos.github.io/get](https://ctlos.github.io/get "https://ctlos.github.io/get")

Предварительно отформатируйте usb накопитель (например в gparted).

#### Кросплатформенные (Linux, Windows).

[https://etcher.io/](https://etcher.io/ "https://etcher.io/")

#### Windows.

Rufus: [https://rufus.akeo.ie/](https://rufus.akeo.ie/ "https://rufus.akeo.ie/")

#### Linux.

Форматирование usb.

    sudo mkfs.vfat /dev/sdX -I

Запись образа dd.

    sudo dd bs=4M if=ctlos.iso of=/dev/sdX status=progress && sync

### Static web

> Static sites work seamlessly in a [Jekyll](/building/jekyll/) build, gaining access to more editing features in CloudCannon.