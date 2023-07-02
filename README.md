Network speed indicator for Unity
=================================

![](https://raw.github.com/mgedmin/indicator-netspeed/master/screenshot.png)

Fix
-----
如果你使用**ubuntu18.04**+的版本，但是依然使用unity桌面，你会发现原来的安装的ppa源也没用了，下载源码也无法编译成功，提示缺少依赖库。
为了解决这个问题，我fork了这个库做了以下修改：

- 依赖库libappindicator3-dev修改成libayatana-appindicator3-dev
- 源码里面第2行include改成： #include <libayatana-appindicator3-0.1/libayatana-appindicator/app-indicator.h>
- Makefile里面的依赖appindicator3-0.1修改成ayatana-appindicator3-0.1

然后就可以成功编译安装了。

Usage
-----

```
sudo apt-get install build-essential libgtop2-dev libgtk-3-dev ibayatana-appindicator3-dev git-core
git clone git://github.com/wangbjun/indicator-netspeed.git
cd indicator-netspeed
make
sudo make install
indicator-netspeed &
```

The indicator will be put left of all your other indicators. If this is undesirable, the ordering
index can be changed in gsettings:/apps/indicators/netspeed (use dconf-editor).


TODO
----

* Configuration options only accessible through dconf-editor, add a simple options menu.
* Allow toggling autostart at login.
* Do some magic when interfaces are added or disappear.
* The Makefile is a bit stupid right now and is probably specific to ubuntu.
* It's not packaged, create deb building scripts.

Credits
-------

Originally written by Marius Gedminas <marius@gedmin.as>

Contributors:

- Tobias Brandt <tob.brandt@gmail.com>
- Stefan Bethge (stefan at lanpartei.de)

