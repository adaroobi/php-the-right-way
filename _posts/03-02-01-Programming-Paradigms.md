---
title: النماذج البرمجية
isChild: true
anchor:  programming_paradigms
---

## النماذج البرمجية {#programming_paradigms_title}

PHP هي لغة مرنة ومتغيرة حيث أنها تدعم عدة أساليب برمجية. فقد تطورت بشكل ملحوظ خلال السنين الماضية وأضافت البرمجة كائنية
التوجه (Object Oriented) في إصدار PHP 5.0 (سنة 2004) وأضافت الدَّوال المجهولة (anonymous functions) ونطاق التسميات (namespaces) في الإصدار PHP 5.3 (سنة 2009) وأضافت السِّمَات (traits) في إصدار PHP 5.4 (سنة 2012).

### البرمجة كائنية التوجه (الشيئية) OOP

تحتوي PHP على خَوَاصِ البرمجة الكائنية بشكل كامل وذلك يشمل الأصناف (class) والأصناف المجردة (abstract class) والمنافذ (interface) والوراثة (inheritance) والبنائيات (constructor) والاستنساخ (clone) والاستثناء (exception) والمزيد ...

* [قراءة المزيد عن البرمجة الشيئية OOP PHP][oop]
* [قراءة المزيد عن السِّأمَات Traits][traits]

### البرمجة الوظيفية

تدعم PHP دوال «المستوى الأول»، بمعنى أنه يمكن إسناد دالة إلى متغير. كل من «دوال المستخدم» والدوال المدمجة مع اللغة يمكن إحالتها باستخدام متغيرات ومناداتها بصورة حيوية. يمكن تمرير الدوال كقيم إلى دوال أخرى (خاصية تسمى _الدوال العليا_ _higher-order Functions_) والدوال نفسها بإمكانها إرجاع دوال أخرى!

الإستدعاء (recursion) الذاتي، وهي خاصية تتيح للدَّالة أن تنادي نفسها، وهي مدعومة من قبل اللغة ولكن معظم الشفرة بلغة PHP تعتمد على التكرار.

الدوال المجهولة (anonymous functions) خاصية موجودة منذ الإصدار PHP 5.3 (سنة 2009، مع دعم «الإغلاق» closures).

أضافت PHP 5.4 إمكانية إسناد دوال مجهولة وكائنات مغلقة لنطاق الكائن وقد تم التطوير للإستدعاءات حتى يمكن استخدامها مع كل الدوال في أي حال.

* أكمل القراءة عن [البرمجة الوظيفية في PHP Functional Programming in PHP](pages/Functional-Programming.html)
* [قراءة المزيد عن الدوال المجهولة Anonymous Functions][anonymous-functions]
* [قراءة المزيد عن الأصناف اللااسمية Closure class][closure-class]
* [قراءة المزيد عن الدوال والكائنات المغلقة أو اللااسمية Closures RFC][closures-rfc]
* [قراءة المزيد عن الدوال القابلة للاستدعاء Callables][callables]
* [قراءة المزيد عن استدعاء الدوال بصورة مجهولة باستخدام الدالة `call_user_func_array()`][call-user-func-array]

### البرمجة التحويلية

تدعم PHP أيضاً عدة أشكال من البرمجة التحويلية (Meta programming) عبر عدة وسائل مثل واجهة برمجة تطبيقات الإنعكاس (reflection API)
والدوال السحرية (Magic Methods). هناك عدة دوال سحرية مثل `__get()`، `__set()`، `__clone()`، `__toString()`، `__invoke()`
وغيرها والتي تتيح للمُطَوِّر ربطها بتصرفات الكائنات. يقول مطورو لغة Ruby أن لغة PHP تفتقر إلى الدالة `method_missing`، ولكنها موجودة
وتتمثل في كل من `__call()` و `__callStatic()`.

* [قراءة المزيد عن الدوال السحرية Magic Methods][magic-methods]
* [قراءة المزيد عن دوال الإنعكاس Reflection][reflection]
* [قراءة المزيد عن التحميل الإضافي Overloading][overloading]


[oop]: http://php.net/language.oop5
[traits]: http://php.net/language.oop5.traits
[anonymous-functions]: http://php.net/functions.anonymous
[closure-class]: http://php.net/class.closure
[closures-rfc]: https://wiki.php.net/rfc/closures
[callables]: http://php.net/language.types.callable
[call-user-func-array]: http://php.net/function.call-user-func-array
[magic-methods]: http://php.net/language.oop5.magic
[reflection]: http://php.net/intro.reflection
[overloading]: http://php.net/language.oop5.overloading

