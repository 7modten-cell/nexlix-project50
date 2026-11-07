NEXLIX — نظام مباريات متصل بـ TheSportsDB + Firebase Hosting
=========================================================

المحتويات
- index.html: واجهة NEXLIX الأصلية بعد إضافة نظام المباريات.
- firebase.json: إعداد Firebase Hosting.
- .firebaserc: ضع معرّف مشروع Firebase الخاص بك بدلاً من YOUR_FIREBASE_PROJECT_ID.

البطولات المفعّلة
- مصر: Egyptian Premier League (4829)
- إنجلترا: English Premier League (4328)
- إسبانيا: Spanish La Liga (4335)
- السعودية: Saudi Pro League (4668)
- أوروبا: UEFA Champions League (4480) و UEFA Europa League (4481)
- إيطاليا: Italian Serie A (4332)

مصدر البيانات والتحديث
- TheSportsDB API v1 بمفتاح الخطة المجانية العام: 123.
- يجلب المشروع مباريات كل بطولة من eventsnextleague.php.
- تحديث تلقائي كل 10 دقائق، مع زر تحديث يدوي وتخزين آخر بيانات في localStorage.
- يتم تقليل التوازي إلى طلبين لتقليل الضغط على حد الخطة المجانية (30 طلباً/دقيقة حسب وثائق المزود).
- الخطة المجانية لا تضمن live scores لحظية؛ شارة «مباشر» تقديرية اعتماداً على حالة الحدث/الوقت والنتيجة المتاحة من المصدر.
- توفر وعدد مباريات كل بطولة مرتبطان بتغطية TheSportsDB؛ إذا لم يرجع المصدر أحداثاً فستظهر رسالة فارغة بدلاً من بيانات وهمية.

النشر على Firebase Hosting
1) ثبّت Node.js و Firebase CLI على جهازك، ثم سجّل الدخول:
   npm install -g firebase-tools
   firebase login
2) افتح مجلد المشروع في الطرفية.
3) أنشئ مشروعاً من Firebase Console ثم استبدل YOUR_FIREBASE_PROJECT_ID داخل .firebaserc بمعرّف مشروعك.
4) نفّذ:
   firebase use --add
   firebase deploy --only hosting
5) افتح رابط Hosting الذي يظهر بعد اكتمال النشر.

تشغيل محلي
- افتح index.html عبر خادم محلي (لا تعتمد على file:// إذا منع المتصفح طلبات الشبكة).
- مثال باستخدام Python: python -m http.server 8080 ثم افتح http://localhost:8080

ملاحظات
- هذا تحديث لقسم المباريات فقط؛ أقسام الأفلام والقنوات ما زالت كما كانت في النسخة المرسلة.
- لا توجد روابط بث تلفزيوني أو فيديو مضافة.
- المفتاح 123 مفتاح عام خاص بـ TheSportsDB v1 المجاني وليس مفتاحاً سرياً.
- قد تتغير تغطية البطولات أو قيود API من مزود البيانات.
