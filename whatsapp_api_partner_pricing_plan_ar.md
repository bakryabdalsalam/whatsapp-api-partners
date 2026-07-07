# خطة الشراكة في واجهة WhatsApp API وخطة أقل سعر

تاريخ البحث: 2026-07-01

النطاق: بناء خطة شراكة لمنصة WhatsApp Business Platform تحافظ على أقل سعر ممكن للرسائل وبأكبر قدر ممكن من الاستقرار، مع الالتزام الكامل بقواعد Meta وWhatsApp الرسمية. كل المراجع في هذا المستند هي روابط رسمية من Meta أو WhatsApp أو Meta for Developers.

## 1. القرار التنفيذي

المسار الموصى به:

1. البدء كـ WhatsApp Tech Provider.
2. بناء منصة Cloud API منخفضة التكلفة تشمل Embedded Signup، وحوكمة القوالب، وتقارير الفوترة والتكلفة، وتوجيه الرسائل لاستغلال نوافذ الخدمة المجانية.
3. الترقية إلى Tech Partner عندما تصبح الأهلية متاحة من Meta.
4. السعي إلى Solution Partner فقط إذا احتجنا إلى إدارة فوترة العملاء من خلال مشاركة خط ائتمان.

السبب: صفحة الشركاء الرسمية من Meta تقسم المنظومة إلى Tech Partners وSolution Partners. دور Tech Providers/Tech Partners هو بناء حلول فوق WhatsApp Business Platform. أما Solution Partners فيقدمون حلولًا شاملة، وهم النوع الذي يمكنه تمديد خط ائتمان للشركات من أجل الدفع.

المصدر الرسمي: https://whatsappbusiness.com/partners/become-a-partner/

## 2. حقيقة التسعير

لا يمكننا إجبار Meta على تثبيت أسعار الرسائل الرسمية. يمكننا جعل تسعير العملاء مستقرًا من خلال:

- تمرير رسوم Meta للرسائل بشفافية من دون إخفائها.
- جعل هامشنا في رسوم SaaS ثابتة، أو رسوم منصة، أو رسوم إعداد، أو دعم، أو تكامل.
- استخدام محرك أسعار يقرأ بطاقة أسعار Meta الحالية حسب الدولة والعملة والفئة وشرائح الحجم.
- تصميم تدفقات الرسائل للاستفادة من رسائل الخدمة المجانية، وردود Utility المجانية، ونوافذ الدخول المجانية.
- تجنب التصنيف الخاطئ للفئات. تصنيف رسالة تسويقية كرسالة Utility ليس استراتيجية لتقليل السعر، بل خطر على السياسات وجودة الحساب.

مصدر التسعير الرسمي: https://whatsappbusiness.com/products/platform-pricing/

مصدر تسعير المطورين وبطاقات الأسعار: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing

## 3. فئات الرسائل

تعرض Meta أربع فئات رسائل في WhatsApp Business Platform: Marketing وUtility وAuthentication وService.

| الفئة | الاستخدام الرئيسي | أمثلة | أثر التسعير | استراتيجية تقليل التكلفة |
|---|---|---|---|---|
| Service | الرد على رسائل العملاء داخل نافذة خدمة العملاء | الإجابة عن الأسئلة، توفر المنتج، دعم الحساب، المساعدة في الحجز | تذكر Meta أن رسائل الخدمة لا يتم تحصيل رسوم عليها داخل نافذة خدمة العملاء لمدة 24 ساعة. يتم تجديد النافذة مع كل رسالة جديدة من المستخدم. | ادفع العملاء لبدء المحادثة أولًا. أنجز أكبر قدر ممكن داخل نافذة 24 ساعة. |
| Utility | تحديثات غير ترويجية مرتبطة بطلب أو إجراء من المستخدم | تأكيد الطلب، تحديث الشحن، تذكير بالدفع، تنبيه حساب، تأكيد الاشتراك أو إلغائه، طلب تقييم | يتم تحصيل الرسوم عند التسليم خارج الحالات المجانية. تذكر Meta أن رسائل Utility المرسلة ردًا على المستخدمين لا يتم تحصيل رسوم عليها. مؤهلة لشرائح الحجم. | انقل التدفقات المعاملاتية الحقيقية إلى قوالب Utility. أرسلها داخل نافذة خدمة العملاء عندما يكون ذلك ممكنًا. |
| Authentication | رموز التحقق وكلمات المرور لمرة واحدة | OTP لتسجيل الدخول، استرداد الحساب، تأكيد معاملة | يتم تحصيل الرسوم لكل رسالة يتم تسليمها. مؤهلة لشرائح الحجم. بعض الأسواق لديها سعر Authentication-International. | استخدمها فقط للـ OTP والأمان. اجمع الحجم للاستفادة من الشرائح عندما يكون ذلك مؤهلًا. |
| Marketing | الرسائل الترويجية، الوعي، التحويل، إعادة الاستهداف، إعادة التفاعل | خصومات، توصيات منتجات، سلة مهجورة، عرض ولاء، بيع إضافي | غالبًا هي الفئة الأعلى تكلفة. لا تستفيد من شرائح Utility/Auth. | استخدمها فقط للمستخدمين الذين وافقوا وبدرجة نية عالية. فضّل نقاط دخول Click-to-WhatsApp عندما تكون مناسبة تجاريًا. |

صفحات الفئات الرسمية:

- Marketing: https://whatsappbusiness.com/products/conversation-categories/marketing/
- Utility: https://whatsappbusiness.com/products/conversation-categories/utility/
- Authentication: https://whatsappbusiness.com/products/conversation-categories/authentication/
- Service: https://whatsappbusiness.com/products/conversation-categories/service/
- تصنيف القوالب: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-categorization

## 4. لقطة أسعار مصر الحالية بالدولار الأمريكي

بطاقة الأسعار الرسمية بالدولار من صفحة تسعير المطورين لدى Meta تحمل وسم "effective July 1, 2026". يجب دائمًا اعتبار الصفحة الرسمية مصدر الحقيقة الحالي، لأن روابط ملفات CSV التي تولدها Meta قد تنتهي صلاحيتها.

أسعار مصر بالدولار الأمريكي لكل رسالة يتم تسليمها:

| السوق | Marketing | Utility | Authentication | Authentication-International | Service |
|---|---:|---:|---:|---:|---:|
| Egypt | 0.0644 | 0.0036 | 0.0036 | 0.0650 | 0.00 عند إرسالها كرسائل خدمة داخل نافذة خدمة العملاء |

المعنى:

- رسائل Marketing في مصر أغلى بحوالي 17.9 مرة من رسائل Utility أو Authentication.
- 100,000 رسالة Marketing تكلف حوالي 6,440 دولار من رسوم Meta.
- 100,000 رسالة Utility تكلف حوالي 360 دولار قبل أي خصومات شرائح حجم أعلى.
- ردود Service داخل نافذة خدمة العملاء يجب اعتبارها مسار أقل سعر لأن Meta لا تفرض رسومًا عليها.

المصدر الرسمي: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing

## 5. شرائح الحجم في مصر لرسائل Utility وAuthentication

توفر Meta شرائح حجم لرسائل Utility وAuthentication. سعر الشريحة ينطبق فقط على الرسائل داخل تلك الشريحة، ولا يطبق بأثر رجعي على كل الرسائل.

شرائح Utility في مصر بالدولار:

| عدد رسائل Utility شهريًا | السعر |
|---:|---:|
| 0 إلى 100,000 | 0.0036 |
| 100,001 إلى 1,000,000 | 0.0034 |
| 1,000,001 إلى 4,500,000 | 0.0032 |
| 4,500,001 إلى 40,000,000 | 0.0031 |
| 40,000,001 إلى 80,000,000 | 0.0029 |
| 80,000,001+ | 0.0027 |

شرائح Authentication في مصر بالدولار:

| عدد رسائل Authentication شهريًا | السعر |
|---:|---:|
| 0 إلى 300,000 | 0.0036 |
| 300,001 إلى 2,000,000 | 0.0034 |
| 2,000,001 إلى 10,000,000 | 0.0032 |
| 10,000,001 إلى 20,000,000 | 0.0031 |
| 20,000,001 إلى 40,000,000 | 0.0029 |
| 40,000,001+ | 0.0027 |

شرائح Authentication-International في مصر بالدولار:

| عدد رسائل Authentication-International شهريًا | السعر |
|---:|---:|
| 0 إلى 300,000 | 0.0650 |
| 300,001 إلى 2,000,000 | 0.0618 |
| 2,000,001 إلى 10,000,000 | 0.0585 |
| 10,000,001 إلى 20,000,000 | 0.0553 |
| 20,000,001 إلى 40,000,000 | 0.0520 |
| 40,000,001+ | 0.0488 |

المصدر الرسمي: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing

## 6. قواعد توجيه الرسائل لأقل سعر

نفذ هذه القواعد في الكود قبل إرسال أي رسالة:

1. إذا أرسل المستخدم لنا رسالة وكانت نافذة خدمة العملاء لمدة 24 ساعة مفتوحة، أرسل رسالة Service عندما يكون الرد دعمًا أو مبيعات أو خدمة.
2. إذا أرسل المستخدم لنا رسالة وكان الرد تحديثًا معاملاتياً حقيقيًا، استخدم قالب Utility داخل النافذة عندما نحتاج إلى قالب.
3. إذا دخل المستخدم من إعلان Click-to-WhatsApp أو زر دعوة لاتخاذ إجراء في صفحة Facebook، استخدم نافذة الدخول المجانية لمدة 72 ساعة عندما تكون مؤهلًا.
4. إذا كانت الرسالة OTP أو رمز تحقق، استخدم Authentication. لا تخلط نص OTP داخل Utility أو Marketing.
5. إذا كان المحتوى يروّج أو يعيد الاستهداف أو يبيع إضافيًا أو يقدم خصومات أو يعيد التفاعل، استخدم Marketing واحصره في المستخدمين الموافقين وذوي النية العالية.
6. خارج نافذة خدمة العملاء، استخدم القوالب المعتمدة فقط، واحسب التكلفة حسب دولة المستلم وفئة القالب.
7. لا ترسل إشعارات مكررة. استخدم مفاتيح idempotency وإيصالات التسليم وحالة الحدث قبل إرسال رسالة أخرى قابلة للفوترة.

المصادر الرسمية:

- التسعير والنوافذ المجانية: https://whatsappbusiness.com/products/platform-pricing/
- قوالب الرسائل: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/overview
- تصنيف القوالب: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-categorization

## 7. تصميم المنتج لأقل تكلفة على العميل

ابن المنتج حول رحلات تبدأ من المستخدم:

- زر WhatsApp في الموقع، رموز QR، صفحات حالة الطلب، الفواتير، التغليف، وروابط البريد يجب أن تطلب من المستخدم بدء محادثة WhatsApp.
- استخدم إعلانات Click-to-WhatsApp عندما يكون الاكتساب المدفوع مبررًا، لأن Meta توضح أنه عندما يرسل المستخدم رسالة من إعلان مؤهل أو CTA في صفحة Facebook، لا يتم تحصيل رسوم على الرسائل في الـ 72 ساعة التالية.
- وجّه الدعم وما قبل البيع والأسئلة المتكررة وتتبع الطلبات والمرتجعات وأسئلة الحساب عبر نافذة خدمة العملاء.
- حوّل زيارات مركز الاتصال ورسائل SMS الخاصة بالحالة إلى تدفقات Utility عندما يكون المحتوى معاملاتياً فعلًا.
- اجعل حملات Marketing أصغر، ومقسمة، ومقاسة بالتحويل لأنها الفئة الأعلى تكلفة.

المصدر الرسمي: https://whatsappbusiness.com/products/platform-pricing/

## 8. نموذج تسعير مستقر للعملاء

استخدم ثلاث طبقات فوترة:

1. رسوم Meta الممررة
   - رسوم Meta الدقيقة حسب الرسائل المسلمة، سوق المستلم، الفئة، وشريحة الحجم.
   - تظهر منفصلة في الفواتير ولوحات المعلومات.

2. رسوم منصة ثابتة
   - يجب أن يأتي هامشنا من اشتراك SaaS، المقاعد، صندوق الوارد، الشات بوت، التحليلات، القوالب، تكامل CRM، دعم SLA، الإعداد، والتدريب.
   - هذا يجعل وعد أقل سعر للرسائل موثوقًا.

3. محفظة مسبقة الدفع أو حد ميزانية اختياري
   - يحدد العملاء حد إنفاق شهري.
   - يوقف النظام الرسائل التسويقية غير الحرجة قبل تجاوز الميزانية.
   - تستمر تدفقات Utility/Auth/Service وفق سياسة العميل.

تجنب:

- هامش مخفي لكل رسالة إذا كانت المهمة هي أقل سعر.
- باقات Marketing غير محدودة إلا إذا احتفظنا بحق التعديل حسب الدولة والفئة.
- الوعد بتثبيت أسعار Meta لفترات طويلة. Meta هي التي تتحكم في بطاقات الأسعار الرسمية.

## 9. مسار الشراكة

### المرحلة A: بناء Cloud API مباشر لأعمالنا

الهدف: إثبات المنتج قبل موافقة الشراكة.

المهام:

- إنشاء/توثيق Meta Business Portfolio.
- إنشاء تطبيق Meta يحتوي على WhatsApp.
- إعداد WhatsApp Cloud API، رقم اختبار، webhooks، قوالب، وتقارير التسليم.
- بناء موجه الرسائل ومحرك الأسعار الأساسي.
- تنفيذ تتبع نافذة خدمة العملاء وتتبع نافذة الدخول المجانية.

المصادر الرسمية:

- نظرة عامة على Cloud API: https://developers.facebook.com/documentation/business-messaging/whatsapp/about-the-platform
- البدء: https://developers.facebook.com/documentation/business-messaging/whatsapp/get-started

### المرحلة B: أن نصبح Tech Provider

الهدف: تمكين الشركات العميلة من الانضمام إلى حلنا.

المهام:

- التقديم عبر مسار WhatsApp Tech Provider.
- اجتياز App Review للحصول على وصول متقدم لصلاحيات WhatsApp المطلوبة.
- تنفيذ Embedded Signup حتى يتمكن العملاء من ربط أصولهم التجارية.
- إضافة تخزين آمن للتوكنات، webhooks، سجلات تدقيق، حذف بيانات، تدفقات دعم، ومعالجة أخطاء.
- إنشاء فيديو App Review يوضح تدفق الانضمام والمراسلة من البداية للنهاية.

المصادر الرسمية:

- Become a Tech Provider: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/get-started-for-tech-providers
- Embedded Signup overview: https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/overview
- Embedded Signup implementation: https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/implementation
- App Review sample submission: https://developers.facebook.com/docs/whatsapp/solution-providers/app-review/sample-submission/

### المرحلة C: الترقية إلى Tech Partner

الهدف: الانتقال من Tech Provider إلى حالة شريك عندما تصبح الأهلية متاحة.

المهام:

- الحفاظ على سجل سياسات نظيف وجودة عملاء وعملية دعم واضحة.
- تتبع العملاء النشطين، جودة الرسائل، أحجام التسليم، معدلات قبول القوالب، ونتائج الأعمال.
- استخدام مسار "Become a Partner" في App Dashboard عندما تتيح Meta أهلية الترقية.

المصدر الرسمي: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/upgrade-to-tech-partner/

### المرحلة D: قرار Solution Partner

الهدف: السعي لهذا المسار فقط إذا احتجنا إلى خدمات شاملة وتحكم في الفوترة.

لماذا هذا مهم:

- صفحة الشركاء من Meta تذكر أن Solution Partners يقدمون حلولًا شاملة ويمكنهم تمديد خط ائتمان للشركات من أجل الدفع.
- إذا بقينا Tech Provider، فالنموذج الأقل تكلفة والأوضح هو أن يدفع العميل رسوم Meta، وندفع نحن رسوم منصة ثابتة.

المصادر الرسمية:

- منظومة الشركاء: https://whatsappbusiness.com/partners/become-a-partner/
- Get started as Solution Partner: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/get-started-for-solution-partners/

## 10. متطلبات الامتثال

قواعد الامتثال الدنيا:

- الحصول على موافقة المستخدم قبل إرسال رسائل قوالب تبدأها الشركة.
- يجب أن توضح الموافقة اسم الشركة ونوع الرسائل التي يوافق المستخدم على استلامها.
- اجعل الرسائل متوقعة وفي وقتها وذات صلة.
- استخدم فئة القالب الصحيحة.
- راقب تقييمات الجودة، الحظر، بلاغات السبام، فشل التسليم، ورفض القوالب.
- وفر تحكمًا في إلغاء الاشتراك للرسائل التسويقية.
- اتبع WhatsApp Business Messaging Policy وCommerce Policy.

المصادر الرسمية:

- Opt-in: https://developers.facebook.com/documentation/business-messaging/whatsapp/getting-opt-in
- About platform and opt-in: https://developers.facebook.com/documentation/business-messaging/whatsapp/about-the-platform
- Policy enforcement: https://developers.facebook.com/documentation/business-messaging/whatsapp/policy-enforcement
- WhatsApp Business Policy: https://www.whatsapp.com/legal/business-policy/
- WhatsApp Commerce Policy: https://www.whatsapp.com/legal/commerce-policy/

## 18. خريطة عالمية لشركاء ومزودي WhatsApp API

آخر تحقق: 2026-07-01

استخدم هذه القائمة لمقارنة السوق خارج مصر. الدليل الرسمي المرجعي هو Meta WhatsApp Business Platform Partner Showcase. يعرض الدليل أكثر من 50 شريكًا موثوقًا ويمكن التصفية حسب المنطقة والصناعة والقدرات، لكنه قد يحتاج إلى تسجيل دخول بحساب Facebook:

https://business.facebook.com/messaging/partner-showcase

قاعدة مهمة: قبل توقيع اتفاق تجاري أو وصف أي شركة بأنها شريك رسمي حالي، يجب إعادة التحقق منها داخل Meta Partner Showcase لأن مستويات الشراكة والمناطق والقدرات قد تتغير.

| # | الشركة | الموقع الرئيسي | المنطقة / التركيز الرئيسي | دليل عام على حل WhatsApp أو الشراكة |
|---:|---|---|---|---|
| 1 | Infobip | https://www.infobip.com/ | CPaaS عالمي، رسائل مؤسسية، أتمتة متعددة القنوات | https://www.infobip.com/whatsapp-business |
| 2 | Twilio | https://www.twilio.com/ | APIs عالمية للمطورين ومنصة اتصالات | https://www.twilio.com/en-us/messaging/channels/whatsapp |
| 3 | Bird / MessageBird | https://bird.com/ | منصة اتصالات عالمية، API، وتسويق/خدمة عبر WhatsApp | https://bird.com/en-us/products/whatsapp/ |
| 4 | Vonage | https://www.vonage.com/ | APIs اتصالات عالمية وتجارب تجارة محادثية | https://www.vonage.com/communications-apis/messages/features/whatsapp/ |
| 5 | Sinch | https://sinch.com/ | CPaaS عالمي، رسائل، تحقق، وتجارب عملاء متعددة القنوات | https://sinch.com/messaging/whatsapp-business-api/ |
| 6 | CM.com | https://www.cm.com/ | أوروبا/عالمي، Messaging API، ومنصة خدمة عملاء | https://www.cm.com/whatsapp/whatsapp-business-platform/ |
| 7 | 360dialog | https://360dialog.com/ | أوروبا/عالمي، وصول مباشر إلى WhatsApp API ومنصة شركاء | https://360dialog.com/whatsapp-api |
| 8 | Gupshup | https://www.gupshup.ai/ | الهند/عالمي، رسائل محادثية ومنصة WhatsApp مؤسسية | https://www.gupshup.ai/whatsapp-api |
| 9 | Wati | https://www.wati.io/ | SMB ومتوسط السوق، منصة نمو على WhatsApp وحضور قوي في آسيا/الهند | https://www.wati.io/whatsapp-business-api/ |
| 10 | respond.io | https://respond.io/ | إدارة محادثات العملاء عالميًا وانضمام عبر WhatsApp Cloud API | https://respond.io/whatsapp-business-api |
| 11 | tyntec | https://www.tyntec.com/ | أوروبا/عالمي، اتصال WhatsApp Business API ورسائل مؤسسية | https://www.tyntec.com/helpcenter/docs/channels/whatsapp-business/self-service/ |
| 12 | Route Mobile | https://routemobile.com/ | الهند/عالمي، CPaaS ومنصة WhatsApp Business للمؤسسات | https://routemobile.com/products/enhanced-business-messaging/whatsapp-business-solution/ |
| 13 | Zenvia | https://zenvia.com/ | أمريكا اللاتينية، Customer Cloud وتجارب عملاء على WhatsApp | https://zenvia.com/en/whatsapp/ |
| 14 | Blip | https://www.blip.ai/ | البرازيل/أمريكا اللاتينية، ذكاء محادثي وأتمتة WhatsApp | https://www.blip.ai/en/whatsapp/ |
| 15 | Yellow.ai | https://yellow.ai/ | أتمتة محادثية مؤسسية عالميًا واستخدامات WhatsApp AI/chatbot | https://yellow.ai/whatsapp-api/ |
| 16 | Haptik | https://www.haptik.ai/ | الهند/عالمي، AI agents ورحلات عملاء على WhatsApp | https://www.haptik.ai/whatsapp-enterprise |
| 17 | Botmaker | https://botmaker.com/ | أمريكا اللاتينية/عالمي، أتمتة WhatsApp وأدوات BSP | https://botmaker.com/en/whatsapp-business-platform-api |
| 18 | SleekFlow | https://sleekflow.io/ | آسيا/عالمي، تجارة اجتماعية متعددة القنوات وWhatsApp AI agents | https://sleekflow.io/en-us/channels-integrations/whatsapp |
| 19 | AiSensy | https://aisensy.com/ | الهند/عالمي، تسويق WhatsApp، بث، أتمتة، SMB ومتوسط السوق | https://aisensy.com/whatsapp-business-api |
| 20 | Interakt | https://www.interakt.shop/ | الهند/عالمي، WhatsApp CRM وتسويق ومبيعات ودعم | https://www.interakt.shop/whatsapp-business-api/ |
| 21 | Clickatell | https://www.clickatell.com/ | عالمي، تجارة عبر المحادثة وحلول WhatsApp API | https://www.clickatell.com/products/whatsapp/ |
| 22 | Plivo | https://www.plivo.com/ | APIs اتصالات عالمية ورسائل WhatsApp | https://www.plivo.com/whatsapp/pricing/ |
| 23 | SendPulse | https://sendpulse.com/ | عالمي، شات بوت SMB وأتمتة تسويق ومزود WhatsApp API | https://sendpulse.com/features/chatbot/whatsapp-business |
| 24 | Trengo | https://trengo.com/ | أوروبا/عالمي، صندوق وارد مشترك وAI agents وخدمة عملاء على WhatsApp | https://trengo.com/products/whatsapp |
| 25 | MessageMedia | https://messagemedia.com/ | أستراليا/APAC، رسائل أعمال، وهي الآن جزء من Sinch | https://support.messagemedia.com/hc/en-us/articles/9224631333903-Social-Messaging-What-are-the-different-ways-to-use-WhatsApp |

طريقة استخدام هذه القائمة:

- مقارنة التموضع التقني: مزودون مثل Twilio و360dialog وBird وInfobip وSinch وCM.com وRoute Mobile وVonage مهمون للمشترين التقنيين.
- مقارنة تسعير وانضمام SMB: Wati وAiSensy وInterakt وSendPulse وTrengo وSleekFlow وrespond.io ومنتجات شبيهة بـ Gallabox توضح كيف يتم بيع الانضمام السريع ولوحات التحكم الجاهزة.
- مقارنة دخول الأسواق الإقليمية: Blip وZenvia وBotmaker وRoute Mobile وGupshup وWati وAiSensy وInterakt نماذج قوية خارج مصر.
- مقارنة وعد السعر المنخفض: 360dialog وPlivo وعدة مزودين API-first يركزون علنًا على الشفافية أو تمرير رسوم Meta. يجب أن ننافس ذلك بإظهار رسوم Meta بشفافية وجعل هامشنا من قيمة المنصة الثابتة.
- مقارنة قدرات المؤسسات: Infobip وSinch وTwilio وVonage وBird وCM.com وRoute Mobile وClickatell مراجع أقوى لـ SLAs، التوجيه متعدد القنوات، التحقق، والتكاملات.

الخلاصة التنافسية لخطتنا:

السوق مزدحم بالفعل. لا يجب أن يكون تميزنا مجرد "نحن نوفر WhatsApp API". يجب أن يكون:

1. تسعير شفاف يمرر رسوم Meta بلا هامش مخفي.
2. نموذج تشغيل عربي أولًا وموجه لمنطقة MENA.
3. ضوابط تكلفة توجه الرسائل بشكل صحيح إلى نوافذ الخدمة وشرائح Utility/Auth.
4. أدوات شركاء ووكالات لانضمام عدة عملاء.
5. امتثال واضح، موافقات Opt-in، مراجعة قوالب، ولوحات إنفاق للعملاء.

## 19. نموذج عمل شبيه بكرزون مع وكيل AI وردود صوتية على WhatsApp

آخر تحقق: 2026-07-07

موقع كرزون العام يعرض المنتج كمنصة عربية لإدارة محادثات العملاء: صندوق وارد واحد لـ WhatsApp وFacebook وInstagram والبريد الإلكتروني ومحادثة الموقع وTelegram وتكاملات API، مع الأتمتة والشات بوت، توزيع المحادثات على الموظفين، التصنيفات والملاحظات الخاصة، التقارير، تطبيقات الجوال، فتح حساب WhatsApp API رسمي، وميزة AI/OpenAI في الباقة الأعلى. التسعير العام على الموقع يظهر كباقات SaaS شهرية حسب عدد الموظفين والقنوات والمميزات، مع باقات قريبة من 49 و99 و399 دولار شهريًا وقت المراجعة.

المصدر الرسمي الذي تمت مراجعته: https://karzoun.chat/

### نموذج العمل الذي يجب أن نبنيه

لا ننسخ العلامة التجارية. ننسخ فئة المنتج:

"منصة SaaS عربية لإدارة عملاء WhatsApp للمبيعات والدعم والأتمتة ووكلاء الذكاء الاصطناعي والرد على الرسائل الصوتية."

يجب أن يحتوي النموذج على أربع طبقات دخل:

1. اشتراك المنصة
   - رسوم شهرية حسب عدد المستخدمين، القنوات، عمق الأتمتة، التقارير، ومستوى الدعم.
   - مثال:
     - Starter: مستخدم أو مستخدمان، رقم WhatsApp واحد، صندوق وارد، تصنيفات، ردود سريعة.
     - Business: 5-10 مستخدمين، توزيع محادثات، منشئ شات بوت، أدوات قوالب وبث، تقارير.
     - Business Pro: 15+ مستخدمًا، وكيل AI، AI للرسائل الصوتية، أتمتة مخصصة، API، دعم مخصص.

2. رسوم WhatsApp/Meta
   - تمرر رسوم Meta كما هي.
   - تعرض الفئة والدولة وحالة الرسالة مجانية/مدفوعة والتكلفة المتوقعة في لوحة العميل.
   - هذا يحافظ على استراتيجية أقل سعر للرسائل.

3. إضافة استخدام AI
   - رسوم منفصلة للردود النصية بالذكاء الاصطناعي، تحويل الصوت إلى نص، وتوليد رد صوتي.
   - استخدم حصصًا مثل عدد محادثات AI أو دقائق صوت مضمّنة ثم رسوم زيادة.
   - هذا يمنع خسارة الهامش عندما يكون استخدام AI عاليًا.

4. الخدمات والشركاء
   - رسوم إعداد لحساب WhatsApp API وتوثيق Meta Business والقوالب والأتمتة.
   - خدمة إعداد شات بوت/AI مدارة.
   - دعم شهري لإدارة الأتمتة للعميل.
   - برنامج وكلاء/شركاء لوكالات التسويق وشركات البرمجيات.

### MVP المقترح

ابدأ WhatsApp-first، وليس omnichannel كامل من اليوم الأول.

وحدات MVP:

- صندوق وارد WhatsApp Cloud API.
- إدارة فريق: إسناد، ملاحظات، تصنيفات، حالة المحادثة، وسجل المحادثات.
- ملف عميل وحقول CRM بسيطة.
- ردود سريعة ومدير قوالب.
- قواعد أتمتة: إسناد لفريق، إضافة تصنيف، إرسال رد، إشعار موظف، إغلاق محادثة.
- وكيل AI نصي للدعم والمبيعات من المستوى الأول.
- وكيل AI للرسائل الصوتية:
  - العميل يرسل voice note على WhatsApp؛
  - النظام يحولها إلى نص؛
  - وكيل AI يجهز أو يرسل الرد؛
  - الرد يكون نصًا أو voice note مولدة.
- تحويل إلى موظف عندما تكون الثقة منخفضة أو الإجراء حساسًا.
- لوحة فوترة: رسوم Meta، استخدام AI، خطة المنصة، وحد الميزانية.

أضف Instagram وFacebook والبريد ومحادثة الموقع وTelegram وتطبيقات الجوال بعد إثبات المنتج في السوق.

### بنية ردود AI النصية

التدفق:

1. مستخدم WhatsApp يرسل رسالة.
2. Meta ترسل webhook إلى خادمنا.
3. الخادم يخزن الحدث والعميل والمحادثة والقناة والرسالة.
4. موجه التكلفة يتحقق من نافذة خدمة العملاء 24 ساعة.
5. منسق AI يحمّل:
   - قاعدة معرفة العميل؛
   - الأسئلة الشائعة؛
   - المنتجات والخدمات؛
   - السياسات؛
   - سياق المحادثة السابق؛
   - ملف العميل؛
   - الأدوات المسموح بها.
6. وكيل AI ينتج إجابة مع درجة ثقة وإجراءات مطلوبة.
7. قواعد الحماية تقرر:
   - إرسال تلقائي؛
   - طلب موافقة موظف؛
   - تحويل لفريق؛
   - سؤال توضيحي للعميل.
8. النظام يرسل الرسالة عبر WhatsApp Cloud API.
9. اللوحة تسجل الإجابة والمصدر وتصنيف التكلفة وملكية الرد AI/موظف.

النمط المقترح للـ AI:

- وكيل يستخدم أدوات للبحث عن الطلبات والحجوزات وتحديث CRM وإنشاء تذاكر والتحويل لموظف.
- استخدام retrieval/file search لكل قاعدة معرفة خاصة بعميل.
- system prompts منفصلة لكل عميل ولكل حالة استخدام.
- سجل تدقيق لكل قرارات AI.

مراجع OpenAI الرسمية:

- Agents SDK: https://developers.openai.com/api/docs/guides/agents
- File search / knowledge base retrieval: https://developers.openai.com/api/docs/guides/tools-file-search
- Tools/function calling: https://developers.openai.com/api/docs/guides/tools

### بنية الرد على الرسائل الصوتية بالذكاء الاصطناعي

بالنسبة لـ WhatsApp voice notes، استخدم chained voice workflow وليس speech-to-speech مباشر.

تدفق voice note الواردة:

1. العميل يرسل رسالة صوتية على WhatsApp.
2. webhook من WhatsApp يحتوي على حدث الرسالة ومرجع media.
3. الخادم يحمل media من endpoint الخاص بـ Meta.
4. نخزن الملف الأصلي في object storage بسياسة احتفاظ واضحة.
5. نرسل الملف إلى speech-to-text.
6. نخزن النص داخل المحادثة.
7. نشغل وكيل AI النصي على النص.
8. نقرر شكل الرد:
   - رد نصي للسرعة والتكلفة الأقل؛
   - رد صوتي إذا فعّل العميل AI voice أو إذا كان العميل يفضل الصوت.
9. إذا كان الرد الصوتي مفعلًا، نولّد TTS من الإجابة المعتمدة.
10. نرفع/نرسل الصوت عبر WhatsApp Cloud API.
11. نحتفظ بالنص والإجابة وmedia ID والتكلفة وحالة الموافقة.

سبب هذا التصميم:

- رسائل WhatsApp الصوتية هي media messages وليست بث ميكروفون مباشر.
- chained voice يعطينا transcript دائم، مراجعة، موافقة، تحكم تكلفة، وامتثال أفضل.
- توثيق OpenAI يوضح أن chained voice pipeline مناسب عندما نحتاج تحكمًا صريحًا في speech-to-text ثم منطق الوكيل ثم text-to-speech.

المراجع الرسمية:

- WhatsApp audio messages: https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/audio-messages
- WhatsApp media: https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media
- WhatsApp webhooks: https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/messages
- OpenAI voice agents: https://developers.openai.com/api/docs/guides/voice-agents
- OpenAI speech-to-text: https://developers.openai.com/api/docs/guides/speech-to-text
- OpenAI text-to-speech: https://developers.openai.com/api/docs/guides/text-to-speech

### قواعد التحويل إلى موظف

لا يجب أن يرد AI على كل شيء تلقائيًا.

الرد التلقائي مسموح في:

- الأسئلة الشائعة.
- معلومات المنتجات.
- تتبع الطلب.
- ساعات العمل والموقع.
- توفر حجز بسيط.
- تأهيل العملاء المحتملين.
- شرح سياسة المرتجعات.

يتطلب موافقة موظف:

- الاسترجاع المالي.
- الإلغاء.
- النصائح القانونية أو الطبية.
- الشكاوى.
- العميل الغاضب.
- نزاعات الدفع.
- التفاوض خارج حدود الأسعار المسموحة.
- أي إجابة بثقة منخفضة أو بدون مصدر واضح.

ممنوع دون صلاحية أداة صريحة:

- أخذ مدفوعات.
- تغيير حالة طلب.
- إلغاء اشتراك.
- تعديل بيانات عميل.
- تقديم وعد خارج السياسة المعتمدة.

### استراتيجية تسعير نسختنا

الباقات المقترحة:

| الباقة | العميل المستهدف | المتضمن | فكرة سعر شهري |
|---|---|---|---:|
| Starter | شركة صغيرة بفريق WhatsApp واحد | رقم WhatsApp واحد، مستخدمان، صندوق وارد، ردود سريعة، تصنيفات، تقارير أساسية | 29-49 USD |
| Growth | فريق دعم/مبيعات نشط | 5 مستخدمين، أتمتة، قوالب، AI نصي أساسي، تحكم بالبث | 79-149 USD |
| Pro AI | شركات تريد دعم AI | 15 مستخدمًا، وكيل AI، قاعدة معرفة، تحويل صوت لنص، إضافة رد صوتي، API | 249-399 USD |
| Enterprise | حجم عال أو فروع متعددة | مستخدمون حسب الاتفاق، SLA، تكاملات مخصصة، دعم مخصص، خيارات نشر خاصة | Custom |

رسوم الاستخدام:

- رسوم Meta WhatsApp: تمرير حسب الدولة والفئة.
- ردود AI النصية: حصة مضمنة + زيادة.
- تحويل الصوت لنص: بالدقيقة أو حصة مضمنة.
- توليد الرد الصوتي: بالدقيقة أو حصة مضمنة.
- التخزين: مدة احتفاظ مضمنة، ومدة أطول برسوم.
- الإعداد: رسوم مرة واحدة للانضمام وبناء الأتمتة.

### خطة تنفيذ 90 يومًا

الأيام 1-15:

- بناء استقبال WhatsApp webhooks.
- بناء إرسال النص والقوالب والصوت.
- إنشاء schema للمحادثات والعملاء.
- بناء واجهة صندوق وارد بسيطة.
- إضافة حقول تكلفة Meta في ledger الرسائل.

الأيام 16-30:

- إضافة الإسناد، التصنيفات، الملاحظات، الحالات، والردود السريعة.
- إضافة مدير القوالب وتتبع نافذة الخدمة.
- إضافة تقارير أساسية.
- إضافة كيانات الفوترة: tenant، plan، seats، AI usage، WhatsApp pass-through cost.

الأيام 31-45:

- إضافة وكيل AI نصي مع قاعدة معرفة لكل عميل.
- إضافة وضع موافقة الموظف وحدود الثقة.
- إضافة أدوات اختبار للبحث عن الطلبات أو CRM.
- إضافة audit logs.

الأيام 46-60:

- إضافة pipeline الرسائل الصوتية: تحميل الصوت، تحويله إلى نص، تخزين transcript، توليد الرد.
- إضافة TTS للرد الصوتي الاختياري.
- إضافة إعدادات العميل: "نص فقط"، "مسودة فقط"، أو "إرسال تلقائي".

الأيام 61-90:

- تجربة مع 3-5 عملاء في قطاعات مختلفة.
- قياس نسبة حل المحادثات، زمن الرد، دقة AI، نسبة التحويل لموظف، إنفاق Meta، وتكلفة AI.
- تجهيز خدمة الإعداد وبرنامج الوكلاء.
- تجهيز مواد Tech Provider / App Review.

### ما الذي يجعل هذا العمل قابلًا للدفاع عنه

- واجهة ودعم عربي أولًا.
- WhatsApp-first مع تحكم تكلفة، وليس برنامج omnichannel عام فقط.
- تسعير شفاف يمرر رسوم Meta.
- وكلاء AI مدربون لكل عميل وليس شات بوت عام.
- دعم الرسائل الصوتية لمستخدمي MENA الذين يفضلون الصوت على الكتابة.
- human-in-the-loop لبناء الثقة.
- نموذج وكالات/وكلاء للنمو أسرع من البيع المباشر فقط.

### المخاطر الرئيسية

| الخطر | لماذا يهم | التحكم |
|---|---|---|
| AI يرسل إجابة خاطئة | يضر ثقة العميل | موافقة موظف، حدود ثقة، إجابات مبنية على مصادر |
| أخطاء تحويل الصوت لنص | اللهجات العربية والضوضاء صعبة | تخزين transcript، سؤال توضيحي، اختبار اللهجات، تحويل للموظف عند انخفاض الثقة |
| مخالفة سياسات WhatsApp | قد تسبب رفض قوالب أو مشاكل جودة الحساب | Opt-in، فئة صحيحة، مراجعة قوالب، حدود Marketing |
| تكلفة AI مخفية | الاستخدام العالي قد يضرب الهامش | حصص AI، overage، لوحة تكلفة لكل عميل |
| قنوات كثيرة مبكرًا | يبطئ MVP | ابدأ WhatsApp-first ثم أضف القنوات بعد الإيراد |
| منافسة منصات ناضجة | كرزون وغيره لديهم مميزات واسعة | التميز بالسعر الشفاف، AI voice، تركيز MENA، وجودة الخدمة |

## 11. بنية النظام

الوحدات المطلوبة:

- وحدة انضمام العملاء: Embedded Signup، بيانات WABA/رقم الهاتف، الصلاحيات، تسجيل webhooks.
- موجه الرسائل: قرار الفئة، قرار النافذة المجانية، قرار تسعير الدولة، قرار الميزانية.
- مدير القوالب: إنشاء القوالب، مراجعة الفئة، حالة الموافقة، الترجمة، الإصدارات.
- محرك الأسعار: استيراد بطاقة الأسعار الرسمية، حساب الشرائح، API للتقدير، API لبنود الفاتورة.
- دفتر الحسابات: أحداث تسليم الرسائل، تصنيف مجاني/قابل للفوترة، رصيد العميل، الفاتورة الشهرية.
- ضوابط الميزانية: حدود العملاء، حدود الحملات، إيقاف طارئ، خنق حملات التسويق.
- مراقبة الجودة: إلغاء الاشتراك، الحظر، بلاغات السبام، معدل التسليم، معدل القراءة، معدل التحويل.
- مراجعة الإدارة: موافقة يدوية على قوالب Marketing الجديدة والحملات عالية الحجم.

البيانات الأساسية التي يجب تخزينها لكل رسالة:

- Customer ID
- WABA ID
- Phone number ID
- دولة/سوق المستلم
- Template ID والفئة
- هل كانت نافذة الخدمة مفتوحة
- هل كانت نافذة الدخول المجانية مفتوحة
- وقت الإرسال
- وقت التسليم
- تصنيف مجاني/قابل للفوترة
- نسخة بطاقة أسعار Meta
- الشريحة المطبقة
- التكلفة المقدرة والتكلفة النهائية

## 12. قواعد حوكمة التكلفة

أنشئ هذه القواعد الداخلية:

- يتم فحص بطاقة الأسعار شهريًا على الأقل وقبل أي عرض سعر للعميل.
- أي تغيير في بطاقة أسعار Meta ينشئ نسخة تسعير داخلية جديدة.
- تعرض عروض الأسعار العبارة: "رسوم Meta تمريرية وقد تتغير عندما تحدث Meta بطاقات الأسعار الرسمية."
- تتطلب حملات Marketing تكلفة مقدرة، جمهورًا مستهدفًا، مصدر موافقة، عائدًا متوقعًا، وموافقة.
- تتطلب تدفقات Utility/Auth مراجعة فئة قبل الإطلاق.
- يحصل كل عميل على لوحة مباشرة تعرض الرسائل المسلمة، المجانية، المدفوعة، تقسيم الفئات، والتكلفة المتوقعة لنهاية الشهر.

## 13. خطة تنفيذ 90 يومًا

الأيام 1-15:

- بناء نموذج Cloud API مباشر.
- استيراد بطاقة أسعار Meta بالدولار.
- تنفيذ حاسبة أسعار مصر.
- تنفيذ تتبع نافذة الخدمة.
- صياغة سياسات الموافقة والقوالب.

الأيام 16-30:

- بناء مدير القوالب وموجه الرسائل.
- إضافة معالجة webhooks للتسليم.
- إضافة نموذج الفواتير ودفتر الحسابات.
- إطلاق اختبار داخلي مع WABA واحد ورقم هاتف واحد.

الأيام 31-60:

- تنفيذ تدفق Embedded Signup.
- تجهيز مواد App Review لمسار Tech Provider.
- إضافة شاشات انضمام العملاء.
- إضافة حدود الميزانية ولوحات أسعار العملاء.

الأيام 61-90:

- التقديم لمتطلبات Tech Provider/App Review.
- تجربة مع 2-3 شركات صديقة.
- قياس مزيج الفئات، نسبة الرسائل المجانية، تكلفة التسليم، معدل قبول القوالب، وإشارات الجودة.
- تحديد ما إذا كنا نحتاج إلى علاقة مع Solution Partner قائم للفوترة أثناء نضج حالة شراكتنا.

## 14. مؤشرات الأداء

مؤشرات التسعير:

- نسبة الرسائل المرسلة كرسائل Service مجانية.
- نسبة رسائل Utility المرسلة داخل نافذة خدمة العملاء.
- تكلفة Marketing لكل تحويل.
- متوسط تكلفة Utility/Auth بعد الشرائح.
- فرق إنفاق العميل الشهري عن التوقعات.

مؤشرات الشراكة والأعمال:

- معدل إكمال Embedded Signup.
- معدل قبول القوالب.
- معدل تسليم الرسائل.
- معدل الحظر/البلاغات.
- زمن استجابة دعم العملاء.
- هامش الربح من رسوم المنصة الثابتة، وليس من هامش مخفي على رسائل Meta.

## 15. المخاطر الرئيسية

| الخطر | الأثر | التخفيف |
|---|---|---|
| تغير أسعار Meta | تغير فواتير العملاء | نسخ بطاقات الأسعار، نموذج تمرير الرسوم، إشعار تسعير شهري |
| استخدام فئة خاطئة | رفض القوالب، مشاكل جودة، قيود حساب | سير مراجعة للقوالب وقواعد تصنيف |
| حجم Marketing زائد | تكلفة عالية وحظر من المستخدمين | تقسيم الجمهور، حدود، موافقة ROI، تحكم إلغاء الاشتراك |
| تأخر موافقة الشراكة | لا يمكن الانضمام على نطاق واسع كما هو مخطط | البدء بـ Cloud API مباشر لأعمالنا، تجربة حذرة، العمل مع Solution Partner قائم عند الحاجة |
| تعقيد الفوترة | نزاعات العملاء | فصل رسوم Meta، رسوم المنصة، الضرائب، وحدود الميزانية |

## 16. التوصية النهائية

يجب أن يكون وعد أقل سعر كالتالي:

"نمرر أسعار رسائل WhatsApp الرسمية من Meta بلا أي هامش مخفي على الرسائل، ونحسن كل تدفق للاستفادة من نوافذ الخدمة المجانية وشرائح Utility/Auth، ونجعل هامشنا التجاري في رسوم منصة شفافة."

في مصر، أقل مسار مدفوع عمليًا هو Utility/Authentication بسعر 0.0036 دولار لكل رسالة يتم تسليمها قبل خصومات الحجم الأعلى، بينما أقل مسار حقيقي هو رسائل Service بسعر 0.00 دولار عندما يبدأ المستخدم المحادثة وترد الشركة داخل نافذة خدمة العملاء.

## 17. روابط المراجع الرسمية

- WhatsApp Business Platform Pricing: https://whatsappbusiness.com/products/platform-pricing/
- Meta Developer Pricing and Rate Cards: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing
- Become a WhatsApp Business Platform Partner: https://whatsappbusiness.com/partners/become-a-partner/
- Become a Tech Provider: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/get-started-for-tech-providers
- Solution Partner overview: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/overview
- Get started as Solution Partner: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/get-started-for-solution-partners/
- Upgrade to Tech Partner: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/upgrade-to-tech-partner/
- Embedded Signup overview: https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/overview
- Embedded Signup implementation: https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/implementation
- App Review sample submission: https://developers.facebook.com/docs/whatsapp/solution-providers/app-review/sample-submission/
- WhatsApp Cloud API get started: https://developers.facebook.com/documentation/business-messaging/whatsapp/get-started
- About WhatsApp Business Platform: https://developers.facebook.com/documentation/business-messaging/whatsapp/about-the-platform
- Marketing messages: https://whatsappbusiness.com/products/conversation-categories/marketing/
- Utility messages: https://whatsappbusiness.com/products/conversation-categories/utility/
- Authentication messages: https://whatsappbusiness.com/products/conversation-categories/authentication/
- Service messages: https://whatsappbusiness.com/products/conversation-categories/service/
- Template fundamentals: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/overview
- Template categorization: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-categorization
- Opt-in: https://developers.facebook.com/documentation/business-messaging/whatsapp/getting-opt-in
- Policy enforcement: https://developers.facebook.com/documentation/business-messaging/whatsapp/policy-enforcement
- WhatsApp Business Policy: https://www.whatsapp.com/legal/business-policy/
- WhatsApp Commerce Policy: https://www.whatsapp.com/legal/commerce-policy/
