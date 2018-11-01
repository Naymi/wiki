---
title: Установка Ctlos
category: Установка
order: 1
post_video: 
post_photo_path: 
comments: true
edit: true

---
Предварительно отформатируйте usb накопитель (например в gparted).

### Кросплатформенные (Linux, Windows).

[https://etcher.io/](https://etcher.io/ "https://etcher.io/")

### Windows.

Rufus: [https://rufus.akeo.ie/](https://rufus.akeo.ie/ "https://rufus.akeo.ie/")

### Linux.

Форматирование usb.

`sudo mkfs.vfat /dev/sdX -I`  
  
Запись.

`sudo dd bs=4M if=ctlos.iso of=/dev/sdX status=progress && sync`

```bash
$ bundle install
$ bundle exec jekyll build
```

These commands are run in the root folder of your site.

> If your `Gemfile` isn’t in the root folder, set the `BUNDLE_GEMFILE` [environment variable](/building/environments/) to tell the Bundler where to find it. Setting this requires that your gems are specified in the `_config.yml` file.

### Static web

> Static sites work seamlessly in a [Jekyll](/building/jekyll/) build, gaining access to more editing features in CloudCannon.

In a legacy CloudCannon static build, files are copied to the live site almost as is. CloudCannon performs optimisations and processes static-specific hosting features on the files.

To force a legacy CloudCannon static build for a site, add a file called `.nojekyll` to the root folder. There's no need to set this except for sites built with legacy static features.