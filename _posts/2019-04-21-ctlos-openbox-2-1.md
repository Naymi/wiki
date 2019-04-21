---
title: Релиз Ctlos Linux — Openbox,i3 v2.1
type: minor
---

Переход на sddm. Удалил atril(pdf-просмотрщик), т.к. появилась зависимость от caja(файловый менеджер). Альтернатива Evince тянет за собой gnome, поэтому тож не то. Оставляю выбор для вас). Ядро linux 5.0.7.

**Добавлено (added):**

- sddm
- sddm-config-editor-git

**Удалено (removed):**

- atril
- lightdm

Полный список пакетов: [packages.both](https://github.com/ctlos/ctlosiso/blob/5e603fbb600c36a7161bd6fb51dd5c50bcd62741/packages.both){:target="_blank"}.