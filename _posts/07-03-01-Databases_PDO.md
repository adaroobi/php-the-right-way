---
title:   لاحقة PDO
isChild: true
anchor:  pdo_extension
---

## لاحقة PDO {#pdo_extension_title}

تعتبر [PDO] مكتبة مجردة للٱتصال بقاعدة البيانات &mdash; تم بنائها في PHP منذ الإصدار 5.1.0 &mdash; بحيث توفر واجهات ٱتصال عادية للعديد من قواعد البيانات المختلفة. مثلا يمكن ٱستخدام نفس الشفرة المصدرية للٱتصال والعمل بقاعدة بيانات MySQL أو SQLite:

{% highlight php %}
<?php
// PDO + MySQL
$pdo = new PDO('mysql:host=example.com;dbname=database', 'user', 'password');
$statement = $pdo->query("SELECT some_field FROM some_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);

// PDO + SQLite
$pdo = new PDO('sqlite:/path/db/foo.sqlite');
$statement = $pdo->query("SELECT some_field FROM some_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);
{% endhighlight %}

لا تقوم PDO بترجمة أو تحويل الٱستعلامات SQL Queries أو مماثلة الخصائص المفقودة، ولكنها بالفعل تتصل بأكثر من نوع من قواعد البيانات بنفس الوجهة البرمجية API.

للأهمية: `PDO` تتيح بسهولة حقن مدخلات خارجية (كالمفاتح ID مثلا) في ٱستعلام SQL Query من دون القلق بشأن تهديدات SQL Injection.
وهذا ممكن بٱستخدام جمل PDO وتقييد وربط القيم PDO Statements.

فلنفترض أن في مصدر PHP نقوم بٱستقبال مفتاح رقمي ID وهو عبارة عن قيمة في ٱستعلام. هذا المفتاح يجب أن يستخدم لٱستخراج بيانات مستخدم من قاعدة البيانات. الطريقة التالية هي الطريقة `الخاطئة` للقيام بهذه العملية:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- خطأ!
{% endhighlight %}

هذا مصدر خاطئ تماماً. فهو يقوم بإدخال قيم خام إلى ٱستعلام SQL. مما يسبب تَعَرُّضك للٱختراق بسهولة باستخدام أسلوب حقن الٱستعلام [SQL Injection]. تصور أن مخترقا قام بإرسال قيمة `ID` عن طريق تنفيذ عنوان مثل `http://domain.com/?id=1%3BDELETE+FROM+users`.
سوف يقوم بإسناد للمتغير `$_GET['id']` القيمة `1;DELETE FROM users` مما يتسبب بحذف جميع سجلات المستخدمين!
عوضاً عن ذلك يجب أن تقوم (بتعقيم) المفتاح ID المدخل بٱستخدام جمل التقييد في PDO.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$id = filter_input(INPUT_GET, 'id', FILTER_SANITIZE_NUMBER_INT); // <-- قم بترشيح بياناتك أولاً (أنظر [ترشيح البيانات](#data_filtering))، مهم جداً خصوصاً لعمليتي INSERT و UPDATE..
$stmt->bindParam(':id', $id, PDO::PARAM_INT); // <-- تلقائياً يتم تعقيم القيم بٱستخدام PDO
$stmt->execute();
{% endhighlight %}

وهذا مصدر صحيح. يتم ٱستخدام تقييد القيم في جملة PDO. فبدورها تقوم تلقائياً بتعقيم المدخل ID قبل أن تقوم بإدراجه لقاعدة البيانات مما يمنع ٱحتمال هجمات SQL Injection.

عند كتابة عمليات مثل INSERT أو UPDATE، يجب (للأهمية القصوى) أن تقوم [بترشيح البيانات](#data_filtering) أولاً ثم بتعقيمها من العناصر الأخرى مثل (حذف أوسم HTML و JavaScript وغيرها..). سيقوم PDO فقط بتعقيم المدخلات لٱستخدامها في SQL وليس لكي تستخدمها أنت في تطبيقك.

* [تعرف على المزيد عن PDO]

يجب عليك أن تكون على دراية بأن ٱتصال قاعدة البيانات يقوم بٱستخدام مصادر وأنه ليس من الغريب ٱستهلاك هذه المصادر بسبب تلك الٱتصالات التي لم تغلق، ولكن هذا شيء معتاد في الكثير من لغات البرمجة الأخرى. بٱستخدام PDO يمكنك إغلاق الٱتصال فقط بحذف الكائن وذلك للتأكد من أن كل الٱرتباطات قد تم حذفها. مثلاً إسنادها للقيم الفارغة NULL. إذا لم تقم بهذا يدوياً فسوف تقوم PHP تلقائياً بإغلاق هذه الٱتصالات عندما يتم تنفيذ المصدر إلا إذا كنت تستخدم ٱتصالات مستمرة بالطبع.

* [تعرف على المزيد عن ٱتصالات PDO]
[pdo]: http://php.net/pdo
[SQL Injection]: http://wiki.hashphp.org/Validation
[Learn about PDO]: http://php.net/book.pdo
[Learn about PDO connections]: http://php.net/pdo.connections
