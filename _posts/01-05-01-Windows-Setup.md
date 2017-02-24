---
title: التنصيب على نظام تشغيل Windows
isChild: true
anchor:  windows_setup
---

## التنصيب على نظام تشغيل Windows {#windows_setup_title}

يمكنك تحميل الملفات التنفيذية من [windows.php.net/download][php-downloads].
بعد تنصيب PHP يفضل إضافة وضبط مسار التنصيب (المسار الذي يحتوي على ملف php.exe داخله) إلى المتغير العام [PATH][windows-path] حتى تتمكن من تشغيل PHP من أي مكان في النظام.

لأغراض التعلم والتطوير المحلي يمكنك استخدام الخادم المُدْمج مع PHP 5.4 أو أعلى، حتى لا تحتاج عملية الضبط مع برامج أخرى للخادم.
إذا كنت تفضل «الكل في واحد» وهي برامج تحتوي على كل الحزم التي قد تحتاجها من خادم ويب وخادم قاعدة بيانات بالإضافة لـ PHP، إذاً
فبرامج مثل [Web Platform Installer][wpi]، [XAMPP][xampp]، [EasyPHP][easyphp]، [OpenServer][openserver] ، [WAMP][wamp]
ستساعدك عند تنصيب بيئة تطوير متكاملة بسرعة على نظام تشغيل Windows. الجدير بالذكر أنَّ هذه الأدوات تختلف قليلاً مما هي عليه على خوادم مرحلة التنفيذ النهائية، فيجب عليك توخي الحيطة والحذر ومراعاة الإختلافات ما بين البيئتين. مثلا تقوم بالتطوير على بيئة عمل Windows ويتم التنفيذ في بيئة نهائية Linux.

إذا كنت تريد تشغيل بيئتك النهائية على نظام تشغيل Windows حينها IIS7 سوف يُوَفِّر لك أداءً عالٍ ومستقرا.
يمكنك استخدام [phpmanager][phpmanager] (إضافة واجهة عمل رسومية لـ IIS7) لإدارة وضبط PHP بكل سهولة.
IIS7 يكون معه FastCGI مدمج وجاهز للاستخدام، كل ما عليك هو ضبط PHP كمعالج (Handler).
للدعم ومصادر أخرى هناك [صفحة مخصصة على iis.net][php-iis] خصيصاً لـPHP.

بشكل عام تشغيل برامجك على بيئات متعددة في مرحلة التطوير والتنفيذ قد يؤدي لظهور أخطاء ومشاكل مختلفة وغريبة..
لذلك عندما تقوم بتنصيب بيئة تطوير على Windows ثم تقوم بتنصيبها على بيئة عمل نهائية Linux (أو أي نظام تشغيل آخر) يجب أخذ استخدام [بيئة تشغيل افتراضية](/#virtualization_title) بعين الاعتبار.

كريس تانكرسلي لديه مقالة ممتازة على مدونته الشخصية للأدوات التي يستخدمها عندما [يقوم بتطوير البرامج على بيئة Windows][windows-tools].

[easyphp]: http://www.easyphp.org/
[phpmanager]: http://phpmanager.codeplex.com/
[openserver]: http://open-server.ru/
[wamp]: http://www.wampserver.com/en/
[php-downloads]: http://windows.php.net/download/
[php-iis]: http://php.iis.net/
[windows-path]: http://www.windows-commandline.com/set-path-command-line/
[windows-tools]: http://ctankersley.com/2015/07/01/developing-on-windows/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[xampp]: http://www.apachefriends.org/en/xampp.html
