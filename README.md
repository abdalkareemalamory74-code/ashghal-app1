# أشغال (Ashghal) - تطبيق الخدمات الميدانية

تطبيق MVP لإدارة الخدمات الميدانية باستخدام React (Vite) + Tailwind CSS + Firebase مع دعم اللغة العربية وواجهة RTL.

## المميزات الرئيسية

- 🔐 **نظام المصادقة**: تسجيل دخول/إنشاء حساب بالبريد الإلكتروني مع إدارة الأدوار
- 👥 **إدارة الأدوار**: مستخدم، مقاول، مدير مع صلاحيات مختلفة
- 📋 **إدارة الطلبات**: إنشاء ومتابعة طلبات الخدمة مع رفع الصور
- 🔄 **التحديثات الفورية**: مزامنة البيانات باستخدام Firestore
- 📱 **واجهة مستجيبة**: تدعم جميع الأجهزة مع تخطيط RTL للعربية
- 🏗️ **لوحة المقاول**: عرض وقبول الطلبات المتاحة
- 👨‍💼 **لوحة الإدارة**: إدارة شاملة للنظام والمستخدمين

## التقنيات المستخدمة

### Frontend
- **React 18** مع TypeScript
- **Vite** للتطوير والبناء السريع
- **Tailwind CSS** للتصميم مع دعم RTL
- **Wouter** للتنقل
- **TanStack Query** لإدارة البيانات
- **Shadcn/ui** لمكونات الواجهة

### Backend
- **Firebase Authentication** للمصادقة
- **Firestore** لقاعدة البيانات
- **Firebase Storage** لتخزين الملفات
- **Firebase Security Rules** للحماية

## إعداد المشروع

### المتطلبات المسبقة
- Node.js 18+ 
- npm أو yarn
- حساب Firebase

### 1. إعداد Firebase Project

1. اذهب إلى [Firebase Console](https://console.firebase.google.com/)
2. أنشئ مشروع جديد أو اختر مشروع موجود
3. فعّل الخدمات التالية:

#### Authentication
- اذهب إلى **Authentication > Sign-in method**
- فعّل **Email/Password** provider
- أضف النطاقات المصرح بها:
  - `localhost` للتطوير المحلي
  - نطاق Replit الخاص بك (سيظهر في عنوان URL)
  - أي نطاقات إضافية للنشر

#### Firestore Database
- اذهب إلى **Firestore Database**
- أنشئ قاعدة بيانات في وضع الاختبار
- اختر المنطقة الأقرب لك

#### Storage
- اذهب إلى **Storage**
- فعّل Firebase Storage
- ابدأ في وضع الاختبار

### 2. الحصول على مفاتيح Firebase

1. اذهب إلى **Project Settings** (أيقونة الترس)
2. في تبويب **General**، انتقل إلى **Your apps**
3. أضف تطبيق ويب جديد (</>)
4. احفظ المفاتيح التالية:
   - `apiKey`
   - `authDomain`
   - `projectId`
   - `storageBucket`
   - `messagingSenderId`
   - `appId`

### 3. إعداد متغيرات البيئة في Replit

1. في Replit، اذهب إلى تبويب **Secrets** (مجلد القفل)
2. أضف المتغيرات التالية:

```env
VITE_FIREBASE_API_KEY=your_api_key_here
VITE_FIREBASE_AUTH_DOMAIN=your_project_id.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_project_id.firebasestorage.app
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
