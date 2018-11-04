---
title: Тиринг
category: Конфигурирование системы
order: 2
permalink:
post_video: 
post_photo_path: 
comments: true
edit: true
---

### Убиваем тиринг на свободных дровах nvidia (nouveau).

Как установить свободные видео драйвера см. [здесь](https://wiki.archlinux.org/index.php/Nouveau){:target="_blank"}.

В **xfce** данную проблему решает compton `pacman -S compton`, с флагами. Добавить в автостарт данную команду.
```bash
compton -b --paint-on-overlay --unredir-if-possible --backend xr_glx_hybrid --vsync drm --glx-swap-method -1 --glx-no-stencil
```