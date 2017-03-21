---
title: الوقت والتاريخ
isChild: true
anchor:  date_and_time
---

## الوقت والتاريخ {#date_and_time_title}

يوجد صنف (أو class) في لغة البرمجة PHP يُسَمَّى DateTime يساعد في عمليات قراءة وكتابة ومقارنة وحساب الوقت والتاريخ.
هناك العديد من الدوال المتعلقة بعمليات الوقت والتاريخ مضمنة في لغة البرمجة PHP، ولكن DateTime يوفرها بواجهة كائنية (أو شيئية Object-Oriented) للعديد من الاستخدامات. يمكن لهذا الصنف التعامل مع النِّطَاقات الزَّمنية، ولكن هذا غير مُدْرَج في هذا الشرح التعريفي القصير.

لكي نبدأ باستخدام DateTime، قم بتحويل صيغة كاملة صحيحة لتاريخ وزمن بصيغة نصية إلى الصنف باستخدام الدالة المصنِعة `createFromFormat()` أو يمكنك البدء بإنشاء كائن جديد باستخدام `new DateTime` وينتج من تنفيذ هذا الأخير الوقت والزمن الحاليين. يمكن استخدام الدالة `format()` لتحويل DateTime إلى صيغة نصية مرة أخرى للتمكن من طباعتها مثلا.

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('Y-m-d') . "\n";
{% endhighlight %}

يمكن إجراء عمليات حسابية باستخدام DateTime وذلك باستخدام صنف  DateInterval.
يحتوي صنف DateTime على دوال مثل `add()` و `sub()` التي تَسْتخدم مُخْرَجات صنف DateInterval كمعطيات.
لا تقم مطلقاً بكتابة دوال للقيام بعمليةِ حسابِ الثواني في اليوم أو حساب الفترة النهارية أو حتى حساب فرق التوقيت الزمني، ولا تقم باستخدام بدائل أخرى بشكل عام. اسْتَخْدِم DateInterval عوضاً عن ذلك.
للقيام بحساب فَرْقِ التاريخ بين تاريخين قم باستخدام الدالة `diff()` فهي تقوم بإرجاع DateInterval وعندها يمكن عرضه واستخدامه بسهولة.

{% highlight php %}
<?php
// نقوم بإنشاء نسخة من $start ثم نقوم بزيادة شهر وستة أيام
$end = clone $start;
$end->add(new DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'الفرق هو: ' . $diff->format('%m شهر, %d يوم (المجموع: %a يوم)') . "\n";
// الفرق هو: 1 شهر, 6 يوم (المجموع: 37 يوم)
{% endhighlight %}

يمكن لكائن DateTime أن يُستخدم لإجراء عملية مقارنة بالطريقة التقليدية باستخدام:

{% highlight php %}
<?php
if ($start < $end) {
    echo "Start هو قبل end!\n";
}
{% endhighlight %}

المثال الأخير يقوم بشرح صنف DatePeriod الذي يستخدم لعمليات التكرار للأحداث المتكررة. يمكنه أخذ كائني DateTime كمعطيات البداية والنهاية وكائن DateInterval لتحديد الحدث الزمني ليقوم بإرجاع كل الأحداث المتطابقة بين التاريخين!

{% highlight php %}
<?php
// اطبع جميع أيام الخميس بين $start و $end
$periodInterval = DateInterval::createFromDateString('first thursday');
$periodIterator = new DatePeriod($start, $periodInterval, $end, DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // اطبع التاريخ لكل خميس
    echo $date->format('Y-m-d') . ' ';
}
{% endhighlight %}

من لواحق واجهات البرمجة (API) المشهورة للغة PHP [Carbon](http://carbon.nesbot.com). تقوم بوراثة كل شيء من صنف DateTime، لتَقُوم بتعديل طفيف على الشفرة البرمجية، ولكن بخواص أخرى إضافية تضم ميزة التعريب بالإضافة لعمليات إضافة وطرح التاريخ بصيغ مختلفة مما يعني أنه يمكن اختبار التطبيق باستخدام تاريخ من اختيارك.

* [Read about DateTime][datetime]
* [Read about date formatting][dateformat] (accepted date format string options)
* [اقرأ المزيد عن DateTime][datetime]
* [اقرأ المزيد عن تنسيق التاريخ][dateformat] (التنسيقات المعتمدة)

[datetime]: http://php.net/book.datetime
[dateformat]: http://php.net/function.date
