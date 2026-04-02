# Veribenim WordPress SDK

![Veribenim Banner](https://veribenim.com/assets/banner.png)

**الحل الأكثر شمولاً لخصوصية البيانات في WordPress | متوافق مع KVKK و GDPR**

[![Latest Version](https://img.shields.io/packagist/v/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![WordPress Version](https://img.shields.io/badge/WordPress-6.0%2B-blue)](https://wordpress.org)
[![PHP Version](https://img.shields.io/badge/PHP-8.1%2B-purple)](https://www.php.net)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Downloads](https://img.shields.io/packagist/dt/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![KVKK Compliant](https://img.shields.io/badge/KVKK-Compliant-red)](https://www.kvk.gov.tr)
[![GDPR Compliant](https://img.shields.io/badge/GDPR-Compliant-blue)](https://gdpr.eu)

---

## ما هو Veribenim؟

Veribenim هو **منصة إدارة الموافقة وخصوصية البيانات الأكثر شمولاً في العالم**، من تطوير Pariette. قم بدمجه بسهولة في مواقع WordPress الخاصة بك لضمان الامتثال القانوني الكامل فيما يتعلق بجمع ومعالجة البيانات الشخصية للزوار.

---

## 🎯 لماذا Veribenim؟

### 1. أكثر حل KVKK شمولاً
تم تصميم Veribenim للالتزام بجميع المتطلبات التي حددتها سلطة حماية البيانات التركية (KVKK). وفقاً للمادة 6، يتم جمع البيانات القائمة على الموافقة وإدارتها ضمن نطاق الموافقة الصريحة. يسجل نظام مسار التدقيق كل موافقة.

### 2. معمارية متوافقة بالكامل مع GDPR
بالنسبة للمواقع التي تعمل في أوروبا، فإن المادة 7 من GDPR (إثبات الموافقة) والمادة 13 (التزام الشفافية) مستوفاة بالكامل. يفي لافتة الموافقة متعددة اللغات بمتطلبات GDPR.

### 3. حقن البرنامج النصي التلقائي
لا يلزم الترميز بعد التثبيت. يقوم Veribenim بحقن حزمة JavaScript تلقائياً في علامات WordPress `<head>`. الاتصالات المشفرة SSL/TLS هي معيار.

### 4. معمارية سهلة الاستخدام للمطورين
خطافات PHP، نقاط نهاية REST API، ونظام خطافات WordPress لـ WordPress بدون رؤوس والتكاملات المخصصة. الرموز القصيرة وكتل Gutenberg تمكن المستخدمين غير التقنيين.

### 5. دعم Multisite والمؤسسة
دعم الرموز المستقلة لكل موقع فرعي في شبكة WordPress Multisite الخاصة بك. إمكانية التكوين العام أو الخاص بالموقع.

### 6. التدقيق وإعداد التقارير في الوقت الفعلي
يتم تسجيل جميع قرارات الموافقة في قاعدة البيانات. يعرض لوحة المسؤول بالتاريخ وعنوان IP الفئات التي تمت الموافقة عليها/رفضها.

### المقارنة: Veribenim مقابل الحلول الأخرى

| الميزة | Veribenim | CookieBot | OneTrust | Cookyes |
|---------|-----------|-----------|----------|---------|
| **متوافق مع KVKK** | ✅ | ❌ | ✅ | ❌ |
| **متوافق مع GDPR** | ✅ | ✅ | ✅ | ✅ |
| **دعم عربي أصلي** | ✅ | ⚠️ محدود | ⚠️ محدود | ✅ |
| **WordPress أصلي** | ✅ | ✅ | ⚠️ نص | ✅ |
| **WooCommerce مدمج** | ✅ | ✅ | ⚠️ | ⚠️ |
| **دعم Multisite** | ✅ | ❌ | ❌ | ❌ |
| **خطافات PHP** | ✅ | ❌ | ❌ | ⚠️ |
| **فريق عربي** | ✅ | ❌ | ❌ | ⚠️ |

---

## 📋 جدول المحتويات

1. [التثبيت](#كيف-يتم-التثبيت)
2. [البدء السريع](#البدء-السريع)
3. [الميزات](#الميزات)
4. [تكامل WooCommerce](#تكامل-woocommerce)
5. [خطافات المطور](#خطافات-المطور)
6. [إعداد Multisite](#إعداد-multisite)
7. [معايير الأمان](#معايير-الأمان)
8. [المتطلبات](#المتطلبات)

---

## 🚀 كيف يتم التثبيت؟

### الطريقة 1: من لوحة إدارة WordPress

1. قم بتسجيل الدخول إلى لوحة التحكم في WordPress
2. انتقل إلى **المكونات الإضافية → إضافة جديد**
3. ابحث عن **"Veribenim"**
4. انقر على **تثبيت → تفعيل**

### الطريقة 2: Composer

```bash
composer require veribenim/wordpress
```

ثم قم بتفعيل المكون الإضافي من لوحة التحكم في WordPress.

### الطريقة 3: التثبيت اليدوي

1. قم بتحميل `veribenim-wordpress.zip` من [صفحة الإصدارات](https://github.com/pariette/veribenim-wordpress/releases)
2. قم بتحميله إلى `wp-content/plugins/`
3. قم بتفعيله من لوحة التحكم

### الإعداد بعد التثبيت

1. انتقل إلى **الإعدادات → Veribenim**
2. انسخ رمز الموقع الخاص بك من [app.veribenim.com](https://app.veribenim.com) → موقعك → التكامل
3. الصق الرمز في حقل **رمز موقع Veribenim**
4. حدد اللغة المفضلة لديك (Türkçe, English, Deutsch, Français, Español, Български, العربية)
5. انقر على **حفظ**

✅ سيظهر لافتة Veribenim الآن على جميع مواقعك.

---

## ⚡ البدء السريع

```php
// عند قبول الموافقة
add_action('veribenim_consent_accepted', function($preferences) {
    // $preferences = ['necessary'=>true, 'analytics'=>true, 'marketing'=>false]
    error_log('تم قبول الموافقة: ' . json_encode($preferences));
});

// عند رفض الموافقة
add_action('veribenim_declined', function() {
    error_log('تم رفض الموافقة');
});

// إضافة البيانات الوصفية للموافقة
add_filter('veribenim_consent_metadata', function($metadata) {
    $metadata['user_role'] = get_current_user()->roles[0] ?? 'guest';
    return $metadata;
});
```

---

## 🎨 الميزات

- **حقن البرنامج النصي التلقائي** — تم حقن حزمة JavaScript تلقائياً في قسم `<head>`
- **لوحة إعدادات الإدارة** — الرمز واللغة وتخصيص اللافتة من صفحة واحدة
- **تصميم مستقل عن المظهر** — يعمل مع جميع موضوعات WordPress
- **متوافق مع WooCommerce** — الموافقة في الدفع والمخزن مع تفاصيل الطلب
- **تحديثات قائمة على AJAX** — تحديث التفضيلات بدون إعادة تحميل الصفحة
- **دعم REST API** — تكامل WordPress بدون رؤوس
- **الكود القصير وكتلة Gutenberg** — دعم الكود القصير `[veribenim_consent]` وكاتب الكتل
- **متوافق مع مكونات التخزين المؤقت** — يعمل مع WP Rocket و W3 Total Cache و LiteSpeed Cache
- **دعم Multisite** — تفعيل الشبكة والتكوين الخاص بالموقع

---

## 🛒 تكامل WooCommerce

على مواقع WooCommerce:
- تم إضافة مربع الموافقة تلقائياً لعملية الدفع
- التفضيلات المحفوظة ببيانات الطلب
- عرض تفاصيل الموافقة في **WooCommerce → الطلبات → [الطلب] → موافقة Veribenim**

---

## 👨‍💻 خطافات المطور

```php
// قبل تحميل لافتة الموافقة
add_action('veribenim_before_load', function() { });

// بعد قبول الموافقة
add_action('veribenim_after_consent', function($preferences) { });

// إضافة فئات موافقة مخصصة
add_filter('veribenim_consent_categories', function($categories) {
    $categories['custom'] = ['label' => 'مخصص', 'description' => 'الوصف'];
    return $categories;
});
```

**نقاط نهاية REST API:**
```bash
GET /wp-json/veribenim/v1/consent/{user_id}
POST /wp-json/veribenim/v1/consent
```

---

## 🌐 إعداد Multisite

1. **مسؤول الشبكة → الإعدادات → Veribenim** — تعيين الرمز العام
2. **لوحة تحكم الموقع الفرعي → الإعدادات → Veribenim** — تكوين الرمز الخاص بك
3. **مسؤول الشبكة → المكونات الإضافية** → **تفعيل عبر الشبكة**

---

## 🔒 معايير الأمان

### توافق KVKK

- ✅ **المادة 6 :** المعالجة على أساس الموافقة
- ✅ **المادة 10 :** حقوق الموضوع
- ✅ **المادة 13 :** التزام الشفافية
- ✅ **المادة 14 :** أمان البيانات

### توافق GDPR

- ✅ **المادة 4 :** مصمم كمنصة لإدارة الموافقة
- ✅ **المادة 7 :** الموافقة الحرة والمحددة والمستنيرة
- ✅ **المادة 13 :** المعلومات المقدمة لموضوع البيانات
- ✅ **المادة 17 :** الحق في النسيان (حق الحذف)
- ✅ **المادة 32 :** أمان المعالجة

### الأمان التقني

- **التشفير :** TLS 1.3 (AES-256-GCM) وقاعدة البيانات AES-256
- **اتصالات API :** HTTPS/TLS 1.3 و Bearer Token و CORS وتحديد السرعة
- **مسار التدقيق :** الطابع الزمني وعنوان IP و User-Agent وسجل التغييرات
- **الشهادات :** ISO 27001 و SOC 2 Type II

### الاحتفاظ بالبيانات

- ملفات تعريف الارتباط المطلوبة: التزام قانوني (غير محدد)
- التحليلات: 30 يوماً
- التسويق: 90 يوماً
- سجل التدقيق: سنة واحدة

---

## 📋 المتطلبات

- **WordPress :** 6.0 أو أحدث
- **PHP :** 8.1 أو أحدث
- **HTTPS :** مطلوب لأمان البيانات
- **الموصى به :** Nginx 1.20+ و PostgreSQL 13+ و 128MB RAM

---

## ❓ الأسئلة الشائعة

**س: هل يمكنني تخصيص Veribenim وفقاً لاحتياجاتي؟**

ج: نعم! قم بتخصيص ألوان اللافتة والموضع والنص من لوحة الإدارة. يستخدم التخصيص المتقدم خطافات PHP وعوامل تصفية.

---

**س: هل يحمي Veribenim بيانات العملاء في WooCommerce؟**

ج: نعم، يعرض Veribenim تلقائياً متطلبات الموافقة عند الدفع WooCommerce ويخزن التفضيلات مع الطلب.

---

**س: هل يؤثر Veribenim على SEO الخاص بي؟**

ج: لا. يتم تحميل Veribenim بشكل غير متزامن ولا يؤثر سلباً على سرعة الصفحة أو درجات Google PageSpeed.

---

**س: هل يمكنني استخدام رموز مختلفة لكل موقع في WordPress Multisite؟**

ج: نعم، يمكن لكل موقع فرعي أن يكون له رمز خاص به أو استخدام الرمز العام من مسؤول الشبكة.

---

**س: ما البيانات التي يخزنها Veribenim؟**

ج: تفضيلات الموافقة والطابع الزمني وعنوان IP فقط. لم يتم تخزين البيانات الشخصية الحساسة (بطاقات الائتمان وأرقام الضمان الاجتماعي وما إلى ذلك).

---

**س: هل يمكنني اختبار Veribenim قبل الالتزام؟**

ج: نعم، نقدم نسخة تجريبية مجانية لمدة 30 يوماً. قم بالتسجيل في [app.veribenim.com](https://app.veribenim.com).

---

## 📚 موارد إضافية

- [وثائق Veribenim الرسمية](https://docs.veribenim.com)
- [دليل KVKK](https://www.kvk.gov.tr)
- [GDPR الرسمي](https://gdpr.eu)
- [مستودع GitHub](https://github.com/pariette/veribenim-wordpress)
- [مدونة Veribenim](https://veribenim.com/blog)

---

## 💬 الدعم

هل لديك أسئلة؟ اتصل بنا:

- **البريد الإلكتروني :** support@pariette.com
- **الموقع الإلكتروني :** https://veribenim.com
- **الدردشة المباشرة :** https://app.veribenim.com/support
- **مشاكل GitHub :** [صفحة المشاكل](https://github.com/pariette/veribenim-wordpress/issues)

---

## 📄 الترخيص

يتم نشر Veribenim WordPress SDK بموجب ترخيص MIT. انظر ملف `LICENSE` للتفاصيل.

---

## 🤝 المساهمة

هل تريد المساعدة في تحسين Veribenim؟ تقارير الأخطاء وطلبات الميزات وطلبات السحب مرحب بها دائماً.

1. شاركe [مستودع GitHub](https://github.com/pariette/veribenim-wordpress)
2. أنشئ فرع ميزة (`git checkout -b feature/AmazingFeature`)
3. قم بإلزام التغييرات الخاصة بك (`git commit -m 'Add AmazingFeature'`)
4. الدفع إلى الفرع (`git push origin feature/AmazingFeature`)
5. فتح طلب سحب

---

**أمّن خصوصية بيانات Veribenim. القضاء على المخاطر القانونية. اكتسب ثقة العملاء.**

*أكثر حل شامل لخصوصية بيانات WordPress في العالم — موثوق وكامل ومتوافق.*

---

**الحالة:** ✅ التطوير النشط | **آخر تحديث:** 2 أبريل 2026
