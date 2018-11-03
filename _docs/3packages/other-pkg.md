---
title: Установка доп. программ
category: Дополнительные пакеты
order: 1
permalink:
post_video: 
post_photo_path: 
comments: true
edit: true
---

> Некоторые пояснения и рекомендации по использованию.

#### Содержание статьи:
- [Steam](/wiki/3packages/other-pkg/#steam)
- [Установка и запуск Tor](/wiki/3packages/other-pkg/#установка-и-запуск-tor)
- [Bluetooth](/wiki/3packages/other-pkg/#bluetooth)
- [Офисные пакеты](/wiki/3packages/other-pkg/#офисные-пакеты)
- [Принтеры](/wiki/3packages/other-pkg/#принтеры)

## Steam
Необходимо раскомментировать репозиторий **multilib** в `/etc/pacman.conf`
```bash
sudo pacman -S steam ttf-liberation lib32-alsa-plugins lib32-curl
```

[wiki.archlinux.org](https://wiki.archlinux.org/index.php/Steam_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)){:target="_blank"}.

Или установите Steam через [Flatpak](/wiki/1install/pkg-manager/#еще-один-из-немногих-иенеджеров-flatpak){:target="_blank"}.

---

## Установка и запуск Tor.
```bash
sudo pacman -S tor torsocks
```

Запуск, остановка сервиса tor.
```bash
sudo systemctl start tor
sudo systemctl stop tor
```

Запуск через tor.
```bash
torify zsh
torify ssh user@blabla -p 22
```

Проверка ip.
```bash
curl --max-time 10 -w '\n' http://ident.me
```

В firefox используйте расширение FoxyProxy.

> В настройках расширения, Добавить новый SOCKS4, ip: 127.0.0.1, port: 9050

Chromium запустите с флагом.

```bash
chromium --proxy-server='socks://127.0.0.1:9050' &
```

Если нужно отредактируйте сервис.

```bash
sudo nano /usr/lib/systemd/system/tor.service
```

```bash
[Service]
User=root
Group=root
Type=simple
```
```bash
sudo chown -R root:root /var/lib/tor/
sudo systemctl daemon-reload
sudo systemctl restart tor
```

---

## Bluetooth.
```bash
sudo pacman -S blueman bluez-utils pulseaudio-bluetooth
sudo systemctl enable bluetooth.service
```

---

## Офисные пакеты.

Wps office.
```bash
yay -S wps-office ttf-wps-fonts wps-office-extension-russian-dictionary --noconfirm
```

Libre office.
```bash
yay -S libreoffice-fresh libreoffice-fresh-ru papirus-libreoffice-theme --noconfirm
```

Openoffice.
```bash
yay -S openoffice openoffice-ru-bin --noconfirm
```

Onlyoffice.
```bash
yay -S onlyoffice-bin --noconfirm
```

---

## Принтеры.
```bash
sudo pacman -S cups cups-pdf cups-pk-helper system-config-printer
sudo systemctl enable org.cups.cupsd.service
```