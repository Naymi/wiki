---
title: Установка Ctlos Linux
category: Установка
permalink:
order: 1
post_video: 
post_photo_path: 
comments: true
edit: true
---
Скачайте iso образ: [https://ctlos.github.io/get](https://ctlos.github.io/get "Скачать Ctlos Linux"){:target="_blank"}

## Запись iso образа на usb накопитель.

Предварительно отформатируйте usb накопитель в fat32, например в **gparted**.

### Программы для записи iso образа.

#### Linux.

Форматирование usb.
```bash
sudo mkfs.vfat /dev/sdX -I
```

Запись образа dd.
```bash
sudo dd bs=4M if=ctlos.iso of=/dev/sdX status=progress && sync
```

#### Кросплатформенные (Linux, Windows).

[https://etcher.io/](https://etcher.io/ "https://etcher.io/"){:target="_blank"}

#### Windows.

Rufus: [https://rufus.akeo.ie/](https://rufus.akeo.ie/ "https://rufus.akeo.ie/"){:target="_blank"}

## Установка.

<div class="embed-responsive embed-responsive-16by9">
	<iframe src="https://www.youtube.com/embed/xaaAoakklfQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Проверка ISO образа.

### Проверка контрольных сумм в Windows.

[raylin.wordpress.com](http://raylin.wordpress.com/downloads/md5-sha-1-checksum-utility/){:target="_blank"}

### В Linux. Проверка MD5.  
`md5sum ctlos_xfce_1.0.0_20181102.iso`

#### Проверка  SHA256.  
`sha256sum ctlos_xfce_1.0.0_20181102.iso`

#### GPG.  
`sudo pacman -S gnupg`

#### Импорт ключа и проверка образа.
```bash
gpg --keyserver keys.gnupg.net --recv-keys 98F76D97B786E6A3
gpg --verify ctlos_xfce_1.0.0_20181102.iso.sig ctlos_xfce_1.0.0_20181102.iso
```

Подробнее о [GnuPG](/wiki/3packages/gnupg){:target="_blank"}.

На этом проверка образа закончена. Я привел несколько способов проверки, можите использовать любой, или все сразу.