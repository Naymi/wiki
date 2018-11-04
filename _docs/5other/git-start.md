---
title: Git Start
category: Прочее
order: 5
permalink:
post_video: 
post_photo_path: 
comments: true
edit: true
---

Конфигурация.
```bash
git config --global user.name "ctlos"
git config --global user.email "ctlos@protonmail.com"
```

Генерация ssh-ключей.
```bash
ssh-keygen -t rsa -b 4096 -C "ctlos@protonmail.com"
```

Забрать ключ в `~/.ssh` имя `id_rsa.pub`.

Инициализация.
```bash
git init
```

Статус.
```bash
git status
```

Игнорирование файлов и каталогов `.gitignore`.

Добавление изменений.
```bash
git add .
git commit -m "test"
```

Создание репозитория на github.com.
```bash
git remote add ctlosiso https://github.com/ctlos/ctlosiso
```

Клонирование.
```bash
git clone https://github.com/ctlos/ctlosiso
```

Ssh.
```bash
git clone git@github.com:ctlos/ctlosiso.git
```

Или ветку.
```bash
git clone -b openbox git@github.com:ctlos/ctlosiso.git
```

Список репозиториев.
```bash
git remote
```

Отправка на github.
```bash
git push ctlosiso master
```

Версия проекта.
```bash
git tag "version1.0"
```

Новая ветка.
```bash
git branch work
```

Просмотр веток локально.
```bash
git branch
```

Просмотр веток и удаленных.
```bash
git branch -a
```

Создание локальных веток из удаленных.
```bash
git branch openbox origin/openbox
git branch xfce origin/xfce
git branch budgie origin/budgie
```

Перемещение по веткам.
```bash
git checkout work
```

Слияние веток. Перед этим переключить ветку.
```bash
git merge work
```

Удаление веток.
```bash
git branch -D work
```

Просмотр изменений.
```bash
git log
```