---
title: Timeshift и rsync
category: Резервное копирование
permalink:
order: 1
post_video: 
post_photo_path: /wiki/images/2backup/timeshift-rsync/timeshift.png
comments: true
edit: true
---
Отличная программа для создания backup-ов и восстановления системы: **Timeshift**.
Установка: `yaourt -S timeshift`.

Интерфейс очень простой, главное правильно настроить исключения. Это нужно для того, чтобы вы не дампили большие и не нужные каталоги вашей системы, т.к. это экономит время и место на диске, а работоспособность сохраняется. В пример могу привести каталог virtualbox, мне например он в копии системы не нужен, т.к. он находится на смонтированом диске и сам смонтированый диск мне не нужен, думаю вы поняли.

Вот мой список правил. Важно, правила исключений должны быть выше домашней директории, измените путем перетаскивания.

![File Browser with Add Files menu open](/wiki/images/2backup/timeshift-rsync/exclude-timeshift.png)