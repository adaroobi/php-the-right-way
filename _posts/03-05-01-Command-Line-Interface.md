---
title: واجهة سطور الأوامر
isChild: true
anchor:  command_line_interface
---

## واجهة سطور الأوامر {#command_line_interface_title}

صُمِّمَت لغة PHP لكتابة تطبيقات الويب، ولكن من المفيد أيضاً التعامل مع برامج واجهة سطور الأوامر (CLI).
برامج PHP المبنية للعمل على سطور الأوامر تساعد على أداء مهام معتادة مثل تجربة ونشر وإدارة البرامج بصورة تلقائية.

تطبيقات PHP التي تعمل على واجهة سطور الأوامر هي برامج قوية لأنها تستخدم مصدر البرنامج مباشرة دون الحاجة لتطوير واجهة ويب مرئية ومَحْمِيَّة. ولكن تأكد من **عدم** وضع تطبيقك الذي يعمل بواجهة سطور الأوامر في مجلد موقعك (حيث يمكن للجميع رؤيته)!

جرب تشغيل أمر PHP هذا من واجهة سطور الأوامر:

{% highlight console %}
> php -i
{% endhighlight %}

يدل خيار `-i` على طباعة بيانات ضبط PHP كما تنفذه دالة [`phpinfo()`][phpinfo] تماماً.

أيضاً خيار `-a` يوفر أوامر تفاعلية مماثلة لشبيهاتها عند ruby IRB و python interactive shell. هنالك عدد من الأوامر والخيارات المفيدة
التي يمكنك الاطلاع عليها أيضاً [command line options][cli-options].

لنقم بتجربة كتابة برنامج ترحيبي سهل بطريقة واجهة سطور الأوامر، قم بإنشاء ملف باسم `hello.php` ثم قم بكتابة الآتي:

{% highlight php %}
<?php
if ($argc !== 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

تقوم PHP بإنشاء متغيرين خاصين بناءَ على القيم التي يعمل بها تطبيقك.
[`$argc`][argc] وهو متغير رقمي يحتوي على *عدد* القيم.
[`$argv`][argv] وهو متغير به مصفوفة تحوتي على *قيمة* كل من القيم.
دائما ما يكون الخيار الأول من القيم هو اسم ملف PHP المراد تنفيذه وفي هذه الحالة هو الملف `hello.php`.
تستخدم دالة `exit()` دون قيمة صفرية لإعلام منفذ الأوامر بأن الأمر قد فشل!.
يمكن الإطلاع على شفرات الخروج من [هنا][exit-codes].

لتنفيذ الملف، قم بفتح نافذة تنفيذ سطور الأوامر ثم قم بكتابة الآتي:

{% highlight console %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [لمعرفة المزيد عن تشغيل PHP من واجهة سطور الأوامر][php-cli]
 * [تعرف على كيفية ضبط نظام التشغيل Windows لتشغيل PHP من نافذة سطور الأوامر][php-cli-windows]


[phpinfo]: http://php.net/function.phpinfo
[cli-options]: http://php.net/features.commandline.options
[argc]: http://php.net/reserved.variables.argc
[argv]: http://php.net/reserved.variables.argv
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&amp;topic=sysexits
[php-cli]: http://php.net/features.commandline
[php-cli-windows]: http://php.net/install.windows.commandline
