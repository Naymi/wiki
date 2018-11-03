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
Скачайте iso образ: [https://ctlos.github.io/get](https://ctlos.github.io/get "Скачать Ctlos Linux")

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

## Проверка ISO образа

### Проверка контрольных сумм в Windows.

http://raylin.wordpress.com/downloads/md5-sha-1-checksum-utility/

### В Linux. Проверка MD5.  
`md5sum Ctlos.iso`

### Проверка  SHA256.  
`sha256sum Ctlos.iso`

### GPG.  
`sudo pacman -S gnupg`

### Импорт ключа и проверка образа.
```bash
gpg --keyserver keys.gnupg.net --recv-keys 98F76D97B786E6A3
gpg --verify Ctlos.iso.sig Ctlos.iso
```

На этом проверка образа закончена, это несколько способов проверки, можите использовать любой, или все сразу.

## Дополнительные команды gpg, для большего понимания.

https://wiki.archlinux.org/index.php/GnuPG_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)

### Генерация.  
`gpg --full-gen-key`

### Просмотр списка ключей.
```
gpg --list-keys
gpg --list-secret-keys
gpg --list-public-keys
```

### Удалить ключ.
```
gpg --delete-secret-keys 812549
gpg --delete-keys 812259
```

### Редактировать ключ.  
`gpg --edit-key mail@example.com`

### Экспорт открытого ключа в текстовом виде.  
`gpg --armor --output pubkey.txt --export 812549`

### Экспорт закрытого ключа в текстовом виде.  
`gpg --armor --output privkey.txt --export-secret-keys 812549`

### Экспорт открытого ключа на keyserver.  
`gpg --keyserver keys.gnupg.net --send-keys 8123459`

### Импорт открытого ключа из файла.  
`gpg --import key.txt`  
или по номеру.  
`gpg --recv keys 98F76D97B786E6A3`

### Импорт закрытого ключа.  
`gpg --allow-secret-key-import --import privkey.txt`

### Импорт открытого ключа с keyserver.  
`gpg --keyserver keys.gnupg.net --recv-keys 98F76D97B786E6A3`

### Поиск.  
`gpg --keyserver keys.gnupg.net --search-keys mail@example.com`

### Обновление.  
`gpg --keyserver keys.gnupg.net --refresh-keys`

### Пример подписи и проверки подписи.
```
gpg --detach-sign --no-armor ctlos.iso
gpg --verify ctlos.iso.sig ctlos.iso
```

### Зашифровать файл.  
`gpg --encrypt-files -r A24F76A41D635F7A secret.tar`

### Расшифровать файл.  
`gpg --decrypt-files secret.tar.gpg`