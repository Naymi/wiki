---
title: Решение проблем
category: Конфигурирование системы
order: 3
permalink:
post_video: 
post_photo_path: 
comments: true
edit: true
---

### Ассоциации файлов.

Это нужно, если у вас открывается файл, или каталог не в той программе. Например, директория в музыкальном проигрывателе.

Распознаем файл.
```bash
xdg-mime query filetype wallpaper.jpg
```

Проверяем дефолтные настройки.
```bash
xdg-mime query default inode/directory
```

Переопределяем.
```bash
xdg-mime default org.gnome.Nautilus.desktop inode/directory
```

Еще пример.
```bash
xdg-mime default vlc.desktop video/mp4
```

---

### Сброс пароля root [Reset_root_password](https://wiki.archlinux.org/index.php/Reset_root_password_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)){:target="_blank"}.