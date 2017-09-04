---
title: التنصيب على نظام تشغيل Mac
isChild: true
anchor:  mac_setup
---

## التنصيب على نظام تشغيل Mac {#mac_setup_title}

يحتوي نظام التشغيل OS X على إصدار PHP ولكنها عادة ما تكون غير حديثة.
فالنسخة OS X Mavericks تحتوي على الإصدار 5.4.17، والنسخة OS X Yosemite تحتوي على الإصدار 5.5.9،
والنسخة OS X El Capitan تحتوي على الإصدار 5.5.29 وSierra 5.6.24. لكن مع انطلاق إصدار PHP 7.1 لم تعد هذه الإصدارات جيدة للاستخدام.

هنالك عدة طرق لتنصيب PHP على نظام تشغيل Mac OS X.

### التنصيب بواسطة Homebrew

[Homebrew] هو عبارة عن مدير تطبيقات لنظام تشغيل Mac OS x، يساعدك على تنصيب PHP وملحقاتها بكل سهولة.
[Homebrew PHP] هو المستودع الذي يحتوي كل ما يتعلق بـ PHP لمدير التطبيقات Homebrew، ويمكنك من تنصيب PHP بكل سهولة.

حتى هذه اللحظة يمكنك تنصيب كل من `php53`، `php54`، `php55`، `php56` ،`php71`، `php70` باستخدام الأمر `brew install`، ويمكنك التحويل
فيما بينهم بتعديل متغير `PATH`. أو يمكنك استخدام [brew-php-switcher][brew-php-switcher] للتحويل التلقائي.

### التنصيب بواسطة Macports

مشروع [MacPorts] هو مشروع مفتوح المصدر يهدف لتصميم نظام سهل الاستخدام لتجميع وتنصيب وتحديث
البرامج المفتوحة المصدر لكل من برامج سطور الأوامر X11، Aqua على نظام تشغيل Mac OS X.

يدعم MacPorts الملفات بلغة الآلة المبنية مسبقاً (Pre-Compiled Binaries) لكيلا تقوم بإعادة بناء كل حزمة من متطلبات
النظام من الملفات المصدرية (tarball files)، فهي توفر لك سهولة تنصيب الحزم خصوصاً عندما لا يحتوي نظامك على إحداها.

حتى هذه اللحظة يمكنك تنصيب كل من `php54`، `php55`، `php56`، `php70`، `php71` باستخدام الأمر `port install` مثلاً:

    sudo port install php56
    sudo port install php71

ويمكنك تشغيل الأمر `select` لتَّحويل بين الإصدارات المتوفرة.

    sudo port select --set php php71

### التنصيب بواسطة phpbrew

[phpbrew] هي إداة لتنصيب وإدارة أكثر من إصدار PHP. فهي أداة مفيدة جداً عندما يتطلب مشروعان إصدارات مختلفة من PHP
وتريد تشغيلهما بدون الحاجة لنظام تشغيل افتراضي.

### التنصيب بواسطة Liip's binary installer

وسيلة أخرى متاحة وهي [php-osx.liip.ch] فهي توفر وسيلة تنصيب لنسخة واحدة لكل من الإصدارات ابتداء من 5.3 حتى 7.1.
تتميز بأنها لا تستبدل ملفات حزمة PHP binaries المدمجة مع نظام Apple، ولكنها تعمل على التنصيب في مكان آخر (/usr/local/php5).

### البناء من المصدر Compile from Source

وسيلة أخرى تمكنك من التحكم بإصدارات PHP وتنصيبها، وذلك عن طريق [بنائها بنفسك][mac-compile].
في هذه الحالة تَأَكَّد من تنصيب [Xcode][xcode-gcc-substitution]، أو["Command Line Tools for XCode"] التابعة
 لـ Apple ويمكن تحميلها ["Command Line Tools for XCode"] من قسم Mac للمطورين (Mac Developer Center).

### تنصيب حلول متكاملة مجمعة «الكل في واحد»

كل الحلول السابق ذكرها تتلخص بأنك تطبق عملية تنصيب PHP بنفسك، وهي لا تشمل تنصيب برامج مثل Apache, Nginx أو حتى خادم SQL.
«الكل في واحد» هي حلول متكاملة مثل [MAMP][mamp-downloads] و [XAMPP][xampp] فهي تقوم بتنصيب كل تلك البرامج وضبطهم معاً، ولكن رغم سهولة التنصيب فإن مثل هذه الحلول تفتقر للمرونة.


[Homebrew]: http://brew.sh/
[Homebrew PHP]: https://github.com/Homebrew/homebrew-php#installation
[MacPorts]: https://www.macports.org/install.php
[phpbrew]: https://github.com/phpbrew/phpbrew
[php-osx.liip.ch]: http://php-osx.liip.ch/
[mac-compile]: http://php.net/install.macosx.compile
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/
[xampp]: http://www.apachefriends.org/en/xampp.html
[brew-php-switcher]: https://github.com/philcook/brew-php-switcher
