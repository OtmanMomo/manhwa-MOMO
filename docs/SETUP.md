# 🚀 دليل الإعداد والتثبيت

## المتطلبات الأساسية

- **Node.js** v18+ ([تنزيل](https://nodejs.org/))
- **npm** أو **yarn** (يأتي مع Node.js)
- **Git** ([تنزيل](https://git-scm.com/))
- **Docker** و **Docker Compose** (اختياري) ([تنزيل](https://www.docker.com/))

---

## الطريقة 1️⃣: التثبيت المحلي (بدون Docker)

### 1. استنساخ المستودع

```bash
git clone https://github.com/OtmanMomo/manhwa-MOMO.git
cd manhwa-MOMO
```

### 2. إعداد Backend

```bash
cd backend

# تثبيت المكتبات
npm install

# إنشاء ملف .env
cp ../.env.example .env

# تعديل .env بإضافة بيانات قاعدة البيانات الخاصة بك
# (انظر أسفل الصفحة للمزيد)

# تشغيل الخادم
npm run dev
```

### 3. إعداد Frontend

في نافذة Terminal جديدة:

```bash
cd frontend

# تثبيت المكتبات
npm install

# إنشاء ملف .env
cp ../.env.example .env

# تشغيل تطبيق الويب
npm run dev
```

### 4. الوصول للتطبيق

- **Frontend:** http://localhost:5173
- **Backend API:** http://localhost:5000

---

## الطريقة 2️⃣: التثبيت باستخدام Docker

### 1. استنساخ المستودع

```bash
git clone https://github.com/OtmanMomo/manhwa-MOMO.git
cd manhwa-MOMO
```

### 2. إعداد ملف البيئة

```bash
cp .env.example .env
```

### 3. تشغيل Docker Compose

```bash
docker-compose up -d
```

سيتم تشغيل جميع الخدمات تلقائياً:
- **Frontend:** http://localhost:5173
- **Backend API:** http://localhost:5000
- **MongoDB:** localhost:27017
- **Redis:** localhost:6379

### 4. إيقاف الخدمات

```bash
docker-compose down
```

---

## إعداد قاعدة البيانات

### MongoDB محلي

#### Windows/Mac/Linux:

```bash
# تثبيت MongoDB
# (اتبع التعليمات من: https://docs.mongodb.com/manual/installation/)

# تشغيل MongoDB
mongod
```

#### باستخدام Docker:

```bash
docker run -d \
  --name manhwa-mongo \
  -p 27017:27017 \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=password \
  mongo:7.0
```

### إنشاء قاعدة البيانات الأولية

```bash
# الاتصال بـ MongoDB
mongo mongodb://admin:password@localhost:27017/admin

# تشغيل سكريبت الإنشاء
use manhwa-momo
db.users.createIndex({ email: 1 }, { unique: true })
db.manga.createIndex({ title: 1 })
```

---

## متغيرات البيئة (.env)

### Backend (.env)

```env
# Server
PORT=5000
NODE_ENV=development

# Database
DATABASE_URL=mongodb://admin:password@localhost:27017/manhwa-momo?authSource=admin

# JWT
JWT_SECRET=your-super-secret-key-that-is-at-least-32-characters-long
JWT_EXPIRE=7d

# Email (اختياري)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASSWORD=your-password
SMTP_FROM=noreply@manhwa-momo.com

# Redis (اختياري)
REDIS_URL=redis://localhost:6379
```

### Frontend (.env)

```env
# API
VITE_API_URL=http://localhost:5000

# App
VITE_APP_NAME=MOMO Manhwa
VITE_APP_DESCRIPTION=منصة متخصصة في المانجا والمانهوا
```

---

## الأوامر المفيدة

### Backend

```bash
# تشغيل بوضع Development
npm run dev

# بناء للإنتاج
npm run build

# تشغيل بوضع Production
npm start

# تشغيل الاختبارات
npm test

# Linting
npm run lint
```

### Frontend

```bash
# تشغيل بوضع Development
npm run dev

# بناء للإنتاج
npm run build

# معاينة Build
npm run preview

# Linting
npm run lint
```

---

## استكشاف الأخطاء

### المشكلة: MongoDB غير متصل

**الحل:**
```bash
# تأكد من تشغيل MongoDB
# Windows:
"C:\Program Files\MongoDB\Server\7.0\bin\mongod.exe"

# Linux/Mac:
brew services start mongodb-community
# أو
sudo systemctl start mongod
```

### المشكلة: Port مستخدم بالفعل

**الحل:**
```bash
# تغيير الـ Port في .env
PORT=5001  # بدلاً من 5000

# أو إيقاف البرنامج المستخدم للـ Port
# Windows:
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# Linux/Mac:
lsof -i :5000
kill -9 <PID>
```

### المشكلة: خطأ في npm install

**الحل:**
```bash
# حذف node_modules و package-lock.json
rm -rf node_modules package-lock.json

# إعادة التثبيت
npm install

# أو استخدام npm cache
npm cache clean --force
npm install
```

---

## التطوير والاختبار

### تشغيل الاختبارات

```bash
cd backend
npm test

cd ../frontend
npm test
```

### Linting والتنسيق

```bash
# Backend
cd backend
npm run lint
npm run format

# Frontend
cd frontend
npm run lint
npm run format
```

---

## النشر

### نشر على Vercel (Frontend)

```bash
npm i -g vercel
vercel

# اتبع التعليمات
```

### نشر على Heroku (Backend)

```bash
# تثبيت Heroku CLI
# (من: https://devcenter.heroku.com/articles/heroku-cli)

heroku login
heroku create manhwa-momo-api
git push heroku main
```

---

## المساعدة والدعم

للمساعدة:
1. افحص [Issues المشروع](https://github.com/OtmanMomo/manhwa-MOMO/issues)
2. اقرأ [التوثيق](../README.md)
3. فتح Issue جديد مع تفاصيل المشكلة

---

**آخر تحديث:** 25 يوليو 2026
