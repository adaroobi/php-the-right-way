---
title: تشفير كلمات المرور
isChild: true
anchor:  password_hashing
---

## تشفير كلمات المرور {#password_hashing_title}

دائماً ما يتم بناء تطبيقات PHP تعتمد على تسجيل دخول مستخدمين. فإسم المستخدم وكلمة المرور يتم حفظهما في قاعدة البيانات
حتى يتم استخدامهما للتحقق من هوية المستخدم عن تسجيل الدخول.

من المهم أن تقوم [_بتشفير_][3] كلمات السر قبل حفظها. تشفير كلمة المرور هو عملية تشفير أحادية الاتجاه لا يمكن استرجاعها
وتنفذ على كلمة مرور المستخدم. يتم انشاء نص محدد المدى لا يمكن فكه. هذا يعني نه ستقوم بمقارنة المحتوى المشفر بمثله للتأكد
من أنهما متطابقين، فسوف يكونا كذلك إذا كانا من نفس المصدر، ولكن لا يمكن معرفة المحتوى الأصلي.
إذا لم يتم تشفير كلمات المرور وتم الوصول غير المصرح به لقاعدة البيانات، فسيكون كل حسابات المستخدمين قد تم السيطرة عليها.
يجب تشفير كلمات المرور بشكل مستقل عن طريق إضافة نص عشوائي [_ملح_][5] لكل كلمة مرور قبل تشفيرها. فذلك يساعد على تجنب هجمات القوامين التي تقوم باستخدام جداول قوس المطر "Rainbow tables" (وهي قائمة عكسية معدة مسبقاً من مجموعة تشفيرات لشفرات كلمات مرور كثيرة الاستخدام).
التشفير والتمليح مهم جدا حيث انه بعض المستخدمين يقوم باستخدام نفس كلمة المرور في عدة أجهزة أو خدمات أخرى وقد تكون جودة كلمات مرورهم غير قوية كفاية.
لحسن الحظ، PHP قد سهلت هذه المهمة!

**تشفير كلمات المرور باستخدام `password_hash`**

في إصدارة PHP 5.5 تم إضافة دالة `password_hash()`. حالياً تستخدم هذه الدالة لوغاريثمية BCrypt، وهي اللوغاريثمية الأقوى حتى
الآن في PHP. ستيم مستقبلاً إضافة الدعم لعدة لوغاريثمات أخرى حسب الحاجة. تم إنشاء مكتبة `password_compat` لإتاحة توافقية
لإصدارات PHP المتقدمة PHP >= 5.3.7.

أدناه سنقوم بتشفير نص، ثم نقوم بمقارنته بنص آخر. بما أن كلا النصين مختلفين، (كلمة مرور صحيحة مقارنة بـ كلمة مرور خاطئة)
ستفشل عملية تسجيل الدخول.

{% highlight php %}
<?php
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    // Correct Password
} else {
    // Wrong password
}
{% endhighlight %}  

`password_hash()` takes care of password salting for you. The salt is stored, along with the algorithm and "cost", as part of the hash.  `password_verify()` extracts this to determine how to check the password, so you don't need a separate database field to store your salts.

* [تعرف المزيد عن `password_hash()`] [1]
* [`password_compat` PHP >= 5.3.7 && < 5.5] [2]
* [Learn about hashing in regards to cryptography] [3]
* [Learn about salts] [5]
* [PHP `password_hash()` RFC] [4]


[1]: http://php.net/function.password-hash
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash
[5]: https://en.wikipedia.org/wiki/Salt_(cryptography)
