---
title: المفهوم الأساسي
isChild: true
anchor:  basic_concept
---

## المفهوم الأساسي {#basic_concept_title}

يمكن شرح هذا المفهوم باستخدام مثال سَهْل.

لدينا صنف `Database` يعتمد على مُحول للتخاطب مع قاعدة البيانات. نقوم بإنشاء المحول في دالة الإنشاء ثم نقوم بحقن ثابت.
هذا يجعل عملية التجربة والإختبار عملية صعبة مما يعني أن الصنف `Database` مرتبط بشدة مع المحول.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct()
    {
        $this->adapter = new MySqlAdapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

يمكن إعادة صياغة هذه الشفرة البرمجية لاستخدام حقن التوابع وفك الإرتباط من التوابع:

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(MySqlAdapter $adapter)
    {
        $this->adapter = $adapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

الآن يمكننا أن نعطي صنفَ `Database` توابعه عن طريق إنشائها بنفسه. ويمكن أيضاً إنشاء دالة تستقبل التابع كقيمة ثم إسنادها مباشرة
أو إذا كان المحول `$adapter` في وصف عام `public property` عندها يمكن إسناده مباشرةً.
