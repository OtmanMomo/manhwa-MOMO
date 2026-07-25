# 🤝 دليل المساهمة

شكراً لاهتمامك بالمساهمة في مشروع MOMO Manhwa! 🎉

## كيفية المساهمة

### 1. الإبلاغ عن الأخطاء (Bug Reports)

إذا وجدت خطأ، يرجى:

1. **تحقق أولاً** من أنه لم يتم الإبلاغ عنه بالفعل في [Issues](https://github.com/OtmanMomo/manhwa-MOMO/issues)

2. **افتح Issue جديد** مع المعلومات التالية:
   - عنوان واضح ومختصر
   - وصف دقيق للخطأ
   - خطوات إعادة الإنتاج
   - السلوك المتوقع والفعلي
   - لقطات شاشة إن أمكن
   - بيئة النظام (OS, Browser, إصدارات, إلخ)

**مثال:**
```
العنوان: خطأ في تحميل الفصول

الوصف:
عندما أحاول تحميل فصل من مانجا معينة، أحصل على رسالة خطأ.

خطوات الإعادة:
1. الذهاب إلى صفحة المانجا
2. النقر على أي فصل
3. ملاحظة الخطأ

السلوك المتوقع:
يجب أن يتم تحميل الفصل بسلاسة

المتصفح: Chrome 120
النظام: Windows 10
```

### 2. اقتراح ميزات جديدة (Feature Requests)

1. **افتح Issue** مع التصنيف `enhancement`
2. **وصف المميزة:**
   - ما المشكلة التي تحلها؟
   - كيف ستكون المميزة؟
   - لماذا تعتقد أنها مهمة؟

**مثال:**
```
العنوان: إضافة خاصية الوضع الليلي

الوصف:
يقضي المستخدمون وقتاً طويلاً على الموقع، خاصة في الليل.
سيكون من الرائع إضافة وضع ليلي لتقليل إجهاد العين.

الاستخدام المتوقع:
- زر في القائمة العلوية للتبديل بين الوضع الفاتح والليلي
- حفظ الاختيار في Local Storage
```

---

## خطوات المساهمة بالكود

### 1. Fork المشروع

انقر على زر **Fork** أعلى يمين الصفحة.

### 2. Clone مستودعك

```bash
git clone https://github.com/YOUR_USERNAME/manhwa-MOMO.git
cd manhwa-MOMO
```

### 3. إنشاء Branch جديد

```bash
# تحديث main branch
git checkout main
git pull origin main

# إنشاء branch جديد
git checkout -b feature/your-feature-name
# أو
git checkout -b fix/bug-name
```

**قواعس تسمية Branches:**
- Features: `feature/feature-name`
- Bug fixes: `fix/bug-name`
- Documentation: `docs/doc-name`
- Refactoring: `refactor/what-was-refactored`

### 4. إجراء التغييرات

```bash
# تعديل الملفات المطلوبة
# ...

# التحقق من الأخطاء
npm run lint

# تشغيل الاختبارات
npm test
```

### 5. Commit التغييرات

```bash
git add .
git commit -m "feat: إضافة ميزة جديدة"
# أو
git commit -m "fix: إصلاح خطأ في التحميل"
```

**قواعد Commit Messages:**
```
<type>: <subject>

<body>

<footer>
```

**الأنواع:**
- `feat:` ميزة جديدة
- `fix:` إصلاح خطأ
- `docs:` تحديثات التوثيق
- `style:` تنسيق الكود (بدون تغيير منطقي)
- `refactor:` إعادة هيكلة الكود
- `perf:` تحسينات الأداء
- `test:` إضافة أو تحديث الاختبارات
- `chore:` تحديثات مختلفة

**مثال:**
```
feat: إضافة خاصية البحث المتقدم

- إضافة حقل البحث في الصفحة الرئيسية
- دعم الفلترة حسب النوع والحالة
- تحسين الأداء باستخدام Debounce

Closes #123
```

### 6. Push إلى GitHub

```bash
git push origin feature/your-feature-name
```

### 7. فتح Pull Request

1. انتقل إلى صفحة مستودعك على GitHub
2. انقر على **Compare & pull request**
3. ملء تفاصيل PR:
   - عنوان واضح
   - وصف التغييرات
   - ربط أي Issues ذات صلة

**قالب PR:**
```markdown
## الوصف
وصف موجز لما يفعله هذا PR

## النوع
- [ ] Bug fix
- [ ] ميزة جديدة
- [ ] تحسين الأداء
- [ ] تحديث التوثيق

## الاختبارات
- [ ] تم اختبار التغييرات محلياً
- [ ] تمرير جميع الاختبارات
- [ ] لا توجد رسائل تحذير

## الملفات المتغيرة
- `path/to/file1.js`
- `path/to/file2.js`

## Issues ذات الصلة
Closes #123
```

---

## معايير الكود

### JavaScript/Node.js

```javascript
// ✅ جيد
function getUserData(userId) {
  return db.users.findById(userId);
}

// ❌ سيء
function gUD(uid) {
  return db.users.findById(uid);
}
```

### القواعد:
- استخدم `const` و `let` بدلاً من `var`
- اتبع camelCase للمتغيرات والدوال
- اتبع PascalCase للـ Classes والـ Components
- أضف تعليقات للأكواد المعقدة
- تجنب الدوال الطويلة جداً

### React/Frontend

```jsx
// ✅ جيد
function MangaCard({ manga }) {
  return (
    <div className="manga-card">
      <img src={manga.cover} alt={manga.title} />
      <h3>{manga.title}</h3>
    </div>
  );
}

// ❌ سيء
const MangaCard = (props) => {
  return (
    <div>
      <img src={props.manga.cover} alt={props.manga.title} />
      <h3>{props.manga.title}</h3>
    </div>
  );
}
```

---

## قائمة فحص قبل الـ Commit

- [ ] اتبعت قواعس المشروع
- [ ] كتبت اختبارات للتغييرات الجديدة
- [ ] مررت جميع الاختبارات: `npm test`
- [ ] فحصت الكود: `npm run lint`
- [ ] حدثت التوثيق إن لزم الأمر
- [ ] وأضفت رسالة commit واضحة
- [ ] لا يوجد debugging code أو console.log

---

## نصائح مفيدة

### اختبار التغييرات محلياً

```bash
# تشغيل المشروع كاملاً
docker-compose up -d

# أو تشغيل كل جزء منفصل
npm run dev  # Backend
npm run dev  # Frontend (في terminal منفصل)
```

### مراجعة التغييرات قبل الـ Commit

```bash
git diff          # عرض جميع التغييرات
git diff file.js  # عرض التغييرات في ملف محدد
```

### تحديث Branch من main

```bash
git fetch origin
git rebase origin/main
```

### حل تضاربات الـ Merge

```bash
# في حالة التضاربات
# 1. حل التضاربات يدوياً
# 2. ثم:
git add .
git rebase --continue
```

---

## قناة الاتصال

- **Issues:** للإبلاغ عن الأخطاء واقتراح الميزات
- **Discussions:** للنقاشات العامة
- **Pull Requests:** لمراجعة التغييرات

---

## الشكر والتقدير 🙏

شكراً لمساهمتك! كل مساهمة تساعد في تحسين المشروع، مهما كانت صغيرة.

---

**آخر تحديث:** 25 يوليو 2026
