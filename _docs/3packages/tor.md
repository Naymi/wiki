---
title: Tor
category: Дополнительные пакеты
order: 1
permalink:
post_video: 
post_photo_path: 
comments: true
edit: true
---

## Установка и запуск Tor.  
`sudo pacman -S tor torsocks`

```
sudo systemctl daemon-reload
sudo systemctl restart tor
```

Запуск, остановка сервиса tor.
```
sudo systemctl start tor
sudo systemctl stop tor
```

Запуск через tor.
```
torify zsh
torify ssh user@blabla -p 22
```

Проверка ip.  
`curl --max-time 10 -w '\n' http://ident.me`

В firefox используйте расширение FoxyProxy.

> В настройках расширения, Добавить новый SOCKS4, ip: 127.0.0.1, port: 9050

Chromium запустите с флагом.  
`chromium --proxy-server='socks://127.0.0.1:9050' &`

Если нужно отредактируйте сервис.  
`sudo nano /usr/lib/systemd/system/tor.service`

```
[Service]
User=root
Group=root
Type=simple
```
```
sudo chown -R root:root /var/lib/tor/
sudo systemctl daemon-reload
sudo systemctl restart tor
```