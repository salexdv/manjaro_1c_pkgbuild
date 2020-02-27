### PKGBUILD 1C MANJARO

#### Подготовка
##### В файле переменные `pkgver` и `pkgrel` заменяем на нужные
``` sh
pkgver=8.3.15  - версия платфоры
pkgrel=1869 - номер релиза
``` 

Если версия платформы  8.3.12.1412 и выше, то в зависимостях вместо *webkitgtk2* указываем *webkitgtk3*
``` sh
depends=('webkitgtk3')
```

Перед сборкой пакета необходимо установить *pkgextract*, *imagemagick* и выше указанный *webkitgtk*
Проверить их наличие можно командой:
``` sh
pacman -Qqe | grep -E 'webkitgtk2|pkgextract|imagemagick'
```

*webkitgtk* нужной версии можно собрать самому, что очень долго, либо установить из стороннего репозитория, например, https://cdn.repo.archlinuxcn.org

В */etc/pacman.conf* добавляем новую строчку:

``` sh 
[archlinuxcn]
Server = https://cdn.repo.archlinuxcn.org/$arch
```
Добавим PGP ключи:
``` sh
sudo pacman -Syy && sudo pacman -S archlinuxcn-keyring
```

Скачиваем *webkitgtk*:
``` sh
sudo pacman -S webkitgtk3
```

#### Сборка
Для сборки закидываем rpm-пакеты в каталог с PKGBUILD, запускаем `updpkgsums` для обновления контрольных сумм, затем сама сборка `makepkg -s`
После окончания сборки устанавливаем полученный пакет в систему
``` sh
sudo pacman -U 1c_enterprise83-8.3.15-1869-x86_64.pkg.tar.xz
```

#### Первый запуск
Пробуем запустить клиента
``` sh
/opt/1C/v8.3/x86_64/1cv8
```

Если при запуске появилась ошибка
> /opt/1C/v8.3/x86_64/libstdc++.so.6: version 'GLIBCXX_3.4.26' not found (required by /usr/lib/libwebkitgtk-3.0.so.0)*

заменяем *libstdc++.so.6* следующей командой:
``` sh
sudo cp /usr/lib/libstdc++.so.6 /opt/1C/v8.3/x86_64/libstdc++.so.6
```

#### Шрифты
Если шрифты "Microsoft Core Fonts" не установлены, можно сделать симлинк на шрифты из Windows. Например,
``` sh
sudo ln -s /diskC/Windows/Fonts /usr/share/fonts/WindowsFonts
```
либо копируем шрифты напрямую в каталог */usr/share/fonts/WindowsFonts*

Обновляем кэш шрифтов
``` sh
fc-cache -f
```

#### Создание ярлыка
```sh
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/opt/1C/v8.3/x86_64/1cv8c ENTERPRISE /s'Server\Base' /n'User' /p'Password'
Categories=Office;Finance;
Name=1C Бухгалтерия
Icon=1cv8c
```