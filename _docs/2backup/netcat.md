---
title: Netcat и ssh
category: Резервное копирование
order: 3
permalink:
post_video: 
post_photo_path: 
comments: true
edit: true
---

## Установка `nc` и `pv`.

```bash
sudo pacman -S gnu-netcat pv
```

## Примеры передач.

```bash
cat dump.iso | pv -b | nc -l 3333

dd if=/dev/sdb5 | gzip -9 | nc -l 3333

tar -czf - /etc/ | pv -b | nc -l 3333
```

## Примеры получения.

```bash
nc 187.187.55.18 3333 | pv -b > dump.iso

nc 187.187.55.18 3333 | pv -b > ddsdb5dump.img.gz

nc 187.187.55.18 3333 | pv -b > dump.tar.gz
```

## Примеры получения ssh-туннель.

```bash
ssh -p 22 -f -L 23333:127.0.0.1:3333 name@187.187.55.18 sleep 10; \
nc 127.0.0.1 23333 | pv -b > ctlos.iso
```

Это нужно в том случае, если нет доступа к порту `3333`. Вся передача шифруется, т.к. ssh.

Создаем мост(туннель) на ip `127.0.0.1`(localhost), на порт `23333`. `-p 22` Это стандартный ssh порт, обычно его меняют). 