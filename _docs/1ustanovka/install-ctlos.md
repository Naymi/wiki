---
title: Установка Ctlos Linux
category: Установка
order: 1
post_video: 
post_photo_path: 
comments: true
edit: true

---
Скачайте iso образ: [https://ctlos.github.io/get](https://ctlos.github.io/get "https://ctlos.github.io/get")

## Запись iso образа на usb накопитель.

Предварительно отформатируйте usb накопитель в fat32, например в **gparted**.

### Программы для записи iso образа.

#### Linux.

Форматирование usb.

    sudo mkfs.vfat /dev/sdX -I

Запись образа dd.

    sudo dd bs=4M if=ctlos.iso of=/dev/sdX status=progress && sync

#### Кросплатформенные (Linux, Windows).

[https://etcher.io/](https://etcher.io/ "https://etcher.io/")

#### Windows.

Rufus: [https://rufus.akeo.ie/](https://rufus.akeo.ie/ "https://rufus.akeo.ie/")

## Установка.

<div class="embed-responsive embed-responsive-16by9">
<iframe src="https://www.youtube.com/embed/xaaAoakklfQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>