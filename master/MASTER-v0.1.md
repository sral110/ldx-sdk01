# LDX Master Specification v0.1
## سند مادر سامانه طراحی یادگیری و طرح درس

**وضعیت:** Draft / قابل بازبینی  
**نسخه:** 0.1.0  
**خانواده محصول:** LDX — Learning Design Engine  
**برنامه مرجع فعلی:** Lesson Designer  
**رابط با SDK:** این سند منبع حقیقت محصول است؛ SDK باید قراردادها، مدل‌ها و نقاط تغییر تعریف‌شده در این سند را اجرا کند.

---

## 0. هدف این سند

این سند قرار نیست فقط «شرح ایده نرم‌افزار» باشد. کارکرد آن چهارگانه است:

1. **منبع حقیقت محصول**: مشخص کند مسئله چیست، محصول برای چه کسی است و چه چیزی را باید حل کند.
2. **قرارداد طراحی آموزشی**: روشن کند یک طرح درس قابل قبول چه ویژگی‌هایی دارد و 17 اصل چگونه در تصمیم‌گیری وارد می‌شوند.
3. **مرز بین ثابت و متغیر**: تعیین کند چه چیزهایی هسته غیرقابل تغییرند و چه چیزهایی باید از طریق Preset، Plugin، Config یا Adapter تغییرپذیر باشند.
4. **ورودی مهندسی SDK و App**: هر قابلیت مهم باید بتواند در SDK به قرارداد، Rule، Plugin، Workflow، Adapter یا Schema تبدیل شود.

قاعده بنیادین این پروژه:

> UI نباید محل دفن منطق آموزشی باشد. منطق آموزشی باید در Master و SDK تعریف شود و UI فقط یکی از مصرف‌کنندگان آن باشد.

---

# 1. مسئله چیست؟

## 1.1 مسئله اصلی

معلمان و مدرسان معمولاً میان سه وضعیت نامطلوب گرفتارند:

- **طرح درس اداری و فرم‌محور**: جدول‌ها و فیلدها پر می‌شوند، اما الزاماً به تصمیم آموزشی بهتر منجر نمی‌شوند.
- **طرح درس تجربه‌محور و ذهنی**: مدرس باتجربه طراحی خوبی انجام می‌دهد، اما منطق تصمیم‌های او مستند، قابل تکرار و قابل انتقال نیست.
- **طرح درس مولدشده با AI**: خروجی سریع و خوش‌خوان تولید می‌شود، اما اغلب عمومی، کم‌عمق، فاقد شناخت واقعی فراگیر، بدون هم‌ترازی قابل اثبات، بدون شواهد رعایت اصول و بدون کنترل منبع است.

در نتیجه مسئله فقط «ساختن متن طرح درس» نیست؛ مسئله این است که:

> چگونه فرایند طراحی تدریس را به یک فرایند تصمیم‌گیری حرفه‌ای، شخصی‌سازی‌شده، شواهدپذیر، قابل ممیزی و قابل تکرار تبدیل کنیم، بدون اینکه اختیار و قضاوت حرفه‌ای مدرس را به نرم‌افزار یا AI واگذار کنیم؟

## 1.2 شکاف موجود

ابزارهای رایج معمولاً یکی یا چند مورد از این کمبودها را دارند:

- از «موضوع درس» مستقیم به «طرح درس نهایی» می‌پرند.
- تفاوت مدرس تازه‌کار و باتجربه را جدی نمی‌گیرند.
- تفاوت کلاس 15 نفره با 40 نفره یا حضوری با آنلاین را در منطق طراحی وارد نمی‌کنند.
- کتاب، جزوه و منابع استاد را فقط به عنوان متن خام می‌بینند، نه منبع دارای محدوده، منشأ و اعتبار.
- هدف، فعالیت، تمرین و ارزشیابی را به‌صورت موجودیت‌های مرتبط مدل نمی‌کنند.
- از کاربر می‌خواهند اصول را تیک بزند، اما شاهدی برای تحقق اصل نمی‌خواهند.
- AI را موتور اصلی قرار می‌دهند؛ در نتیجه تغییر Provider یا قطع اینترنت محصول را ناکارآمد می‌کند.
- خروجی خوب را با ظاهر خوب اشتباه می‌گیرند.
- امکان بازاندیشی پس از اجرا و ساخت نسخه بعدی طرح را ندارند.
- تصمیم‌های طراحی و سیر اصلاحات را ثبت نمی‌کنند.

---

# 2. ضرورت محصول

ضرورت LDX از پنج جهت تعریف می‌شود:

## 2.1 ضرورت آموزشی
کیفیت طرح درس به مجموعه‌ای از تصمیم‌های به‌هم‌پیوسته وابسته است: شناخت فراگیر، هدف، انتخاب محتوا، بار شناختی، فعالیت، تمرین، ارزشیابی، بازخورد، انتقال، تفاوت‌های فردی، زمان و بازاندیشی. ابزار باید این ارتباط‌ها را حفظ کند، نه اینکه آن‌ها را به فیلدهای مستقل تبدیل کند.

## 2.2 ضرورت حرفه‌ای مدرس
محصول باید مدرس را **قوی‌تر** کند، نه وابسته‌تر. کاربر باید بعد از چند بار استفاده بهتر بتواند:
- هدف بنویسد،
- خطاهای رایج را پیش‌بینی کند،
- هم‌ترازی را ببیند،
- فعالیت مناسب انتخاب کند،
- و طرح خود را نقد کند.

پس سامانه هم ابزار تولید است و هم ابزار تربیت مهارت طراحی.

## 2.3 ضرورت عصر AI
AI تولید متن را ارزان کرده است؛ در نتیجه مزیت یک محصول حرفه‌ای دیگر «توانایی تولید متن» نیست. مزیت باید در این موارد باشد:
- ساختار تصمیم‌گیری،
- کنترل کیفیت،
- شخصی‌سازی،
- منشأ و ردیابی،
- ممیزی،
- حفظ عاملیت مدرس،
- و قابلیت کار مستقل از مدل خاص.

## 2.4 ضرورت فنی
اگر منطق آموزشی در یک HTML یا UI خاص hard-code شود، هر توسعه بعدی نیازمند بازنویسی است. وجود Master + SDK باعث می‌شود:
- برنامه‌های جدید روی یک موتور مشترک ساخته شوند،
- اصول و قواعد نسخه‌بندی شوند،
- تست‌های ثابت داشته باشیم،
- و توسعه به‌صورت افزایشی انجام شود.

## 2.5 ضرورت حریم خصوصی و دسترسی
بسیاری از منابع آموزشی خصوصی، دارای حق نشر، سازمانی یا شخصی‌اند. محصول باید Offline-first باشد و ارسال فایل به سرویس بیرونی فقط با اقدام آگاهانه کاربر انجام شود.

---

# 3. تعریف محصول

## 3.1 تعریف کوتاه

**LDX Lesson Designer** یک دستیار حرفه‌ای طراحی تدریس است که مدرس را از «شناخت موقعیت و منبع» تا «طراحی، ممیزی، اجرا و بازنگری» هدایت می‌کند و کیفیت طرح را بر اساس یک مجموعه اصول قابل نسخه‌بندی و قابل توسعه ارزیابی می‌کند.

## 3.2 چیزی که محصول نیست

LDX در نسخه پایه:
- جایگزین LMS نیست.
- صرفاً Lesson Plan Generator نیست.
- جایگزین تخصص موضوعی مدرس نیست.
- صحت علمی محتوا را بدون منبع معتبر تضمین نمی‌کند.
- نباید بدون اجازه، فایل کاربر را به سرویس بیرونی ارسال کند.
- نباید AI را شرط کارکرد اصلی قرار دهد.
- نباید مدرس را مجبور به یک Wizard خطی واحد کند.
- نباید «امتیاز کلی» را جای تحلیل تفصیلی کیفیت قرار دهد.

---

# 4. مخاطبان

## 4.1 مخاطب اصلی: مدرس/معلم

پروفایل مدرس نباید فقط با «نقش» تعریف شود. حداقل ابعاد:

- حوزه تدریس: مدرسه / دانشگاه / حوزه / آموزش سازمانی / کارگاه / آزاد
- سابقه طراحی تدریس: تازه‌کار / متوسط / باتجربه / خبره
- میزان آشنایی با اصول آموزشی
- میزان تمایل به راهنمایی نرم‌افزار
- سبک کار: سریع / ساختاریافته / عمیق / پژوهش‌محور
- میزان استفاده از AI
- نیاز به منابع و ارجاع
- نیاز به خروجی رسمی یا اجرایی

## 4.2 فراگیر

پروفایل فراگیر باید حداقل شامل این محورها باشد:

- سن یا مقطع
- سطح پیش‌دانسته
- اندازه گروه
- ناهمگنی
- انگیزه
- توان خواندن/نوشتن متناسب با درس
- نیازهای دسترس‌پذیری
- تجربه قبلی با موضوع
- محدودیت‌های زمانی یا فنی
- نوع مشارکت مورد انتظار

## 4.3 مخاطبان ثانویه

- طراح آموزشی
- سرگروه و ناظر آموزشی
- مدرس تربیت معلم
- مدیر گروه آموزشی
- مدیر مدرسه یا مؤسسه
- پژوهشگر آموزش
- توسعه‌دهنده‌ای که روی SDK برنامه می‌سازد

## 4.4 اصل شخصی‌سازی

هیچ «نقش» منفردی نباید مستقیماً یک طرح درس را تعیین کند. مسیر شخصی‌سازی باید تابع ترکیب زیر باشد:

```
Instructor + Learner + Context + Content + Constraints + Purpose
                         ↓
              Principle Profile
                         ↓
                 Design Path
```

---

# 5. واحد اصلی طراحی: Teaching Context

هر پروژه باید یک Context صریح داشته باشد. حداقل داده‌ها:

- عنوان درس/جلسه
- حوزه و موضوع
- زمان جلسه
- نوع کلاس: حضوری / آنلاین / ترکیبی
- تعداد فراگیر
- امکانات
- امکان کار گروهی
- امکان آزمایش/دست‌ورزی
- محدودیت فضا
- محدودیت برنامه درسی
- محدودیت ارزشیابی
- زبان
- سطح رسمیت
- هدف جلسه: معرفی / آموزش مفهوم / تمرین / تثبیت / انتقال / جمع‌بندی / ارزیابی / حل مسئله

Context یک فرم تزئینی نیست؛ هر فیلد باید یا:
1. بر Rule اثر بگذارد،
2. بر Recommendation اثر بگذارد،
3. یا از مدل حذف شود.

---

# 6. منابع و سیاست منبع

## 6.1 انواع منبع

سامانه باید منبع را به‌عنوان Entity مستقل مدل کند:

- Textbook
- Teacher Notes
- Curriculum / Syllabus
- Article / Research
- Slide / Presentation
- Previous Lesson Plan
- Assessment Bank
- Web Source
- User Text
- Other

## 6.2 محدوده منبع

پس از بارگذاری منبع، کاربر باید محدوده مورد استفاده را مشخص کند:
- صفحه
- فصل
- بخش
- انتخاب متن
- یا کل فایل

طراحی نباید به‌صورت پیش‌فرض کل کتاب را وارد Context یک جلسه کند.

## 6.3 Provenance

هر قطعه استخراج‌شده باید در صورت امکان دارای این اطلاعات باشد:

```
sourceId
page / range
section
chunkId
contentType
extractionMethod
confidence
```

هر پیشنهاد AI یا Rule که مستقیماً از منبع نتیجه شده است باید قابلیت بازگشت به منشأ را داشته باشد.

## 6.4 حالت‌های استفاده از دانش

پروژه باید یک Source Policy داشته باشد:

- **strict-source**: فقط منابع انتخاب‌شده
- **source-first**: منبع اصلی است؛ دانش عمومی فقط با برچسب
- **open-knowledge**: استفاده از دانش بیرونی مجاز است
- **research-mode**: جست‌وجو و افزودن منبع جدید مجاز است

سامانه نباید بدون اطلاع کاربر بین این حالت‌ها جابه‌جا شود.

---

# 7. هسته آموزشی: Principle Pack

## 7.1 اصل بسته‌پذیری

17 اصل فعلی، **Default Principle Pack v1** هستند؛ نه قوانین ابدی hard-coded.

SDK باید امکان ثبت Principle Pack جدید یا نسخه جدید را داشته باشد.

## 7.2 17 اصل پیش‌فرض

1. شناخت فراگیر و نقطه شروع
2. هدف یادگیری روشن و قابل مشاهده
3. هم‌ترازی هدف، فعالیت و ارزشیابی
4. انتخاب و اولویت‌بندی محتوا
5. مدیریت بار شناختی
6. سازمان‌دهی مسیر یادگیری و داربست‌بندی
7. فعال‌بودن شناختی فراگیر
8. تمرین متناسب با هدف
9. بررسی مستمر فهم
10. بازخورد قابل اقدام
11. تثبیت و بازیابی
12. انتقال یادگیری
13. تفاوت‌های فردی و دسترس‌پذیری
14. معنا، انگیزش و سطح مناسب چالش
15. واقع‌بینی زمانی و ریتم درس
16. انعطاف‌پذیری در اجرا
17. بازاندیشی پس از اجرا

## 7.3 وضعیت هر اصل

هر اصل در یک پروژه می‌تواند این ویژگی‌ها را داشته باشد:

- activation: on / off / auto
- importance: 0..3
- minimumLevel: 0..3
- targetLevel: 0..3
- locked: true/false
- overrideAllowed: true/false
- rationale
- evidence[]
- warnings[]
- recommendations[]

## 7.4 قاعده مهم

«خاموش کردن اصل» با «کاهش عمق اجرای اصل» یکی نیست. برخی اصول ممکن است در یک Application Profile قابل خاموش‌شدن نباشند، اما سطح اجرای آن‌ها تغییر کند.

مثلاً در Lesson Designer، موارد زیر به‌صورت پیش‌فرض Core هستند:
- P01 Context
- P02 Goals
- P03 Alignment
- P04 Content Prioritization
- P05 Cognitive Load
- P07 Active Learning
- P08 Practice
- P09 Understanding Check
- P15 Time Feasibility

این فهرست باید در Config قابل نسخه‌بندی باشد، نه در UI.

---

# 8. سطح طراحی: Bronze / Silver / Gold

نام‌ها قابل تغییرند؛ معنای مهندسی آن‌ها باید ثابت بماند.

## 8.1 Bronze — Rapid / حداقل حرفه‌ای
برای طراحی روزمره و کم‌زمان. هسته ضروری حذف نمی‌شود، اما:
- داده ورودی کمتر،
- توصیه کمتر،
- شواهد حداقلی،
- ممیزی کوتاه‌تر.

## 8.2 Silver — Standard / استاندارد
مسیر پیشنهادی پیش‌فرض:
- پروفایل کامل‌تر،
- هم‌ترازی صریح،
- نقاط بررسی فهم،
- مدیریت زمان،
- حداقل یک سازوکار انتقال/بازیابی متناسب.

## 8.3 Gold — Deep / عمیق
برای درس‌های مهم، مدرس تازه‌کار، کلاس دشوار یا نمونه آموزشی:
- تحلیل پیش‌دانسته و بدفهمی،
- شواهد بیشتر،
- مقایسه گزینه‌های طراحی،
- سناریوی جایگزین،
- UDL عمیق‌تر،
- ریسک‌های اجرا،
- ممیزی تفصیلی،
- بازاندیشی ساخت‌یافته.

**اصل ثابت:** Bronze نباید «طرح بد» باشد. تفاوت در عمق طراحی است، نه حذف کیفیت پایه.

---

# 9. مسیرهای اصلی کاربر

سامانه نباید فقط یک Wizard داشته باشد. Workflow باید Graph-based و قابل تعویض باشد.

## 9.1 Create
ساخت طرح جدید از صفر یا از منبع.

## 9.2 Audit
ورود یک طرح موجود و ممیزی آن بر اساس Principle Pack.

## 9.3 Adapt
سازگارکردن طرح موجود برای:
- زمان جدید،
- گروه جدید،
- تعداد فراگیر جدید،
- سطح دشواری جدید،
- فضای آنلاین/حضوری،
- یا محدودیت جدید.

## 9.4 Reflect & Revise
ثبت اجرای واقعی و ساخت Revision بعدی.

## 9.5 Source-first
شروع از کتاب/جزوه و استخراج محدوده، مفاهیم، پیش‌نیازها، مثال‌ها و فعالیت‌های موجود.

## 9.6 Quick Capture
برای مدرس خبره که می‌خواهد در چند دقیقه تصمیم‌های کلیدی را ثبت کند و سپس فقط ممیزی بگیرد.

---

# 10. موجودیت‌های اصلی Domain

حداقل Entityهای هسته:

```
Project
InstructorProfile
LearnerProfile
TeachingContext
Source
SourceSegment
LessonScope
LearningGoal
ContentUnit
Misconception
Activity
Practice
Assessment
FeedbackPlan
TimeBlock
Constraint
PrincipleProfile
Evidence
Recommendation
AuditResult
Preset
Workflow
Reflection
Revision
AIProposal
ExportArtifact
```

## 10.1 Stable ID

همه موجودیت‌های مهم باید Stable ID داشته باشند. تغییر متن نباید هویت Entity را عوض کند.

نمونه:
```
goal-001
activity-004
assessment-003
source-002
evidence-p03-001
```

---

# 11. هم‌ترازی

Alignment یک صفحه نمایشی نیست؛ یک رابطه Domain است.

حداقل روابط:

```
Goal ↔ Content
Goal ↔ Activity
Goal ↔ Practice
Goal ↔ Assessment
```

SDK باید بتواند تشخیص دهد:
- Goal بدون Activity
- Goal بدون Assessment
- Activity بدون Goal
- Assessment بدون Goal
- تفاوت آشکار سطح شناختی Goal و Assessment
- تراکم بیش از حد Activityها روی یک Goal و رهاشدن Goal دیگر

ماتریس Alignment باید از داده واقعی تولید شود، نه دستی.

---

# 12. Evidence و Audit

## 12.1 اصل شواهد

هیچ اصل نباید فقط با Checkbox «رعایت شد» تلقی شود.

برای هر Principle:
- چه Evidenceهایی معتبرند؟
- حداقل شواهد چیست؟
- چه چیزی Warning است؟
- چه چیزی Error است؟
- کدام مورد فقط Recommendation است؟

## 12.2 خروجی ممیزی

هر نتیجه ممیزی:

```
principleId
status: pass | warn | fail | not-applicable
level
evidence[]
gaps[]
recommendations[]
severity
explanation
```

## 12.3 امتیاز کلی

نسخه پایه نباید کاربر را به یک عدد واحد وابسته کند. اگر Score ساخته می‌شود:
- باید همراه Breakdown باشد،
- وزن‌ها قابل مشاهده باشند،
- و Fail حیاتی نباید پشت میانگین خوب پنهان شود.

---

# 13. نقش AI

## 13.1 اصل معماری
AI یک **Adapter و Copilot** است، نه Core Engine.

## 13.2 وظایف مناسب AI

AI می‌تواند:
- اهداف پیشنهادی بسازد،
- فعالیت‌های جایگزین پیشنهاد کند،
- بدفهمی‌های محتمل را استخراج کند،
- محتوا را خلاصه کند،
- طرح را نقد کند،
- Prompt برای Providerهای دیگر بسازد،
- یا پیشنهادهای اصلاحی تولید کند.

## 13.3 وضعیت خروجی AI

هر خروجی AI باید یکی از این وضعیت‌ها را داشته باشد:
- proposed
- accepted
- edited
- rejected

و در صورت امکان:
- provider
- model
- timestamp
- inputContextRefs
- sourceRefs

ثبت شود.

## 13.4 عاملیت مدرس

سامانه نباید پیشنهاد AI را بی‌صدا به طرح قطعی تبدیل کند. در نقاط اثرگذار آموزشی، پذیرش یا ویرایش کاربر باید صریح باشد.

## 13.5 Provider Independence

SDK باید Provider Adapter داشته باشد:
- OpenAI
- Gemini
- Claude
- Local Model
- Manual Copy/Paste
- Future Provider

هیچ منطق Principle نباید به Provider خاص وابسته شود.

---

# 14. Offline-first و حریم خصوصی

## 14.1 قاعده پایه
بدون اینترنت باید بتوان:
- پروژه ساخت،
- داده را ذخیره کرد،
- Principle Profile ساخت،
- طرح را ویرایش کرد،
- Alignment را دید،
- Audit پایه را اجرا کرد،
- خروجی گرفت.

## 14.2 ارسال بیرونی
ارسال فایل، متن یا Context به AI یا API فقط با اقدام آشکار کاربر.

## 14.3 Storage
برای برنامه کامل:
- IndexedDB: پروژه‌ها، فایل‌ها، segmentها و نسخه‌ها
- localStorage: ترجیحات کوچک UI
- Export: JSON / package قابل حمل

## 14.4 امنیت داده
- داده پروژه JSON-compatible باشد.
- فایل یا متن کاربر برای parse شدن execute نشود.
- HTML ورودی sanitize شود.
- Pluginهای کدنویسی‌شده از داده پروژه جدا باشند.

---

# 15. UX حرفه‌ای

## 15.1 اصل
«ساده بودن» به معنای «کم‌عمق بودن» نیست. UI باید **progressive complexity** داشته باشد:
- تازه‌کار راهنمایی بیشتری ببیند.
- خبره بتواند مستقیم و فشرده کار کند.
- اطلاعات تخصصی پنهان نشوند؛ فقط در سطح مناسب نمایش داده شوند.

## 15.2 دو حالت تجربه
- Guided Mode
- Expert Mode

## 15.3 آموزش Just-in-Time
اصول به شکل یک دوره اجباری قبل از طراحی نمایش داده نشوند. آموزش در لحظه نیاز:
- تعریف کوتاه
- مثال خوب/بد
- دلیل هشدار
- امکان مطالعه عمیق‌تر

## 15.4 UIهای کلیدی
- Context Dashboard
- Source Viewer + Scope Selector
- Goal Editor
- Alignment Matrix
- Timeline Simulator
- Principle Profile
- Evidence Inspector
- Live Audit Panel
- AI Proposal Review
- Version/Revision Compare
- Export Center

---

# 16. زمان و امکان اجرا

هر Activity و TimeBlock باید زمان داشته باشد یا قابل برآورد باشد.

Engine باید:
- مجموع زمان را با زمان جلسه مقایسه کند،
- زمان انتقال بین فعالیت‌ها را لحاظ کند یا حداقل هشدار دهد،
- در صورت Overflow پیشنهاد کاهش/ادغام بدهد،
- و نسخه کوتاه‌تر بسازد بدون اینکه هسته آموزشی ناخواسته حذف شود.

---

# 17. Preset

Preset یک تنظیم UI نیست؛ یک بسته پیکربندی است.

Preset می‌تواند شامل:
- Principle weights
- locked principles
- Workflow
- input requirements
- default activity patterns
- source policy
- AI policy
- audit thresholds
- output templates
- UX density

Presetهای اولیه:
- School General
- University Seminar
- Hawza Text Lesson
- Skills Workshop
- Large Class
- Online Class
- Conceptual Lesson
- Practice-heavy Lesson
- Review Session
- First Session

کاربر و سازمان باید بتوانند Preset شخصی بسازند.

---

# 18. خروجی‌ها

سامانه باید Artifactهای مختلف تولید کند، نه فقط یک «طرح درس نهایی»:

1. Full Lesson Plan
2. Teacher Run Sheet
3. One-page Summary
4. Lesson Timeline
5. Alignment Matrix
6. Principle Audit Report
7. Evidence Map
8. Source Map
9. AI Prompt Package
10. Project JSON
11. Reflection Report
12. Revision Diff
13. در آینده: Interactive Lesson Export / kelas-zende Adapter

---

# 19. بازاندیشی و Revision

پس از اجرا، کاربر باید بتواند حداقل این داده‌ها را ثبت کند:

- کجا زمان کم/زیاد آمد؟
- کدام هدف محقق نشد؟
- کدام فعالیت خوب/بد عمل کرد؟
- چه بدفهمی تازه‌ای مشاهده شد؟
- کدام گروه از فراگیران مشکل داشت؟
- چه چیزی باید جلسه بعد تغییر کند؟

هر تغییر باید Revision بسازد، نه اینکه نسخه قبلی را نابود کند.

---

# 20. Event Model

رویدادهای طراحی برای Audit، تحلیل مسیر و توسعه آینده ثبت می‌شوند.

نمونه:

```
project.created
source.added
source.scoped
goal.created
goal.updated
activity.created
assessment.linked
principle.profile.changed
principle.overridden
audit.run
audit.warning.raised
audit.warning.resolved
ai.proposal.created
ai.proposal.accepted
ai.proposal.edited
export.created
reflection.recorded
revision.created
```

Event Log در حالت آفلاین محلی است و ارسال Telemetry پیش‌فرض نباید فعال باشد.

---

# 21. قرارداد Master با SDK

Master باید به Configهای قابل خواندن توسط SDK تبدیل شود.

حداقل سطوح:

```
ProductFamilyConfig
ApplicationProfile
PrinciplePack
PresetPack
WorkflowPack
SourcePolicy
AIPolicy
AuditPolicy
OutputProfile
UIProfile
StoragePolicy
IntegrationProfile
```

SDK باید بتواند بدون تغییر Core:
- Principle جدید ثبت کند،
- Workflow جدید اضافه کند،
- Preset جدید اضافه کند،
- Source Adapter جدید اضافه کند،
- AI Provider جدید اضافه کند،
- Exporter جدید اضافه کند.

---

# 22. ثابت‌ها، متغیرها و Extension Points

## 22.1 Core Invariants
این‌ها به‌سادگی نباید قابل تغییر باشند:
- Versioned schema
- Stable entity IDs
- Source provenance contract
- Principle contract
- Evidence contract
- Audit result contract
- Event envelope
- Revision history
- Offline baseline
- explicit AI acceptance for consequential changes

## 22.2 Configurable
بدون تغییر کد Core:
- عنوان و برند
- نقش‌ها و Audience presets
- سطح Bronze/Silver/Gold و نام آن‌ها
- Principle weights
- locked principles
- Workflow
- فرم Context
- Prompt templates
- Audit thresholds
- Output templates
- UI density
- source policy

## 22.3 Extensible via Plugin/Adapter
- Principle module
- Rule
- Source parser
- OCR
- AI provider
- Exporter
- Storage backend
- Integration bridge
- Activity recommendation library
- Theme / Design System package

---

# 23. کیفیت محصول

محصول بر اساس این ابعاد ارزیابی می‌شود:

1. **Pedagogical validity**
2. **Context fit**
3. **Alignment**
4. **Feasibility**
5. **Source fidelity**
6. **Traceability**
7. **Teacher agency**
8. **Accessibility**
9. **Privacy**
10. **Extensibility**
11. **Reliability**
12. **Explainability**

---

# 24. Acceptance Criteria پایه

نسخه‌ای از Lesson Designer فقط وقتی قابل قبول است که:

- بدون AI قابل استفاده باشد.
- بدون اینترنت Core آن کار کند.
- پروژه Import/Export شود.
- هر Goal بتواند ارتباطش با Activity و Assessment را نشان دهد.
- Audit برای هر Principle وضعیت و Evidence نشان دهد.
- User بتواند دلیل Recommendation را ببیند.
- Source-grounded mode منشأ محتوا را حفظ کند.
- پیشنهاد AI بدون پذیرش کاربر قطعی نشود.
- زمان طرح با زمان جلسه کنترل شود.
- Revision قبلی حفظ شود.
- Preset بدون دستکاری Core قابل افزودن باشد.
- حداقل یک Golden Project در تست‌ها وجود داشته باشد.

---

# 25. سنجه‌های موفقیت

## محصول
- Completion rate مسیر طراحی
- زمان لازم برای رسیدن به طرح قابل اجرا
- تعداد هشدارهای حل‌شده
- نسبت Goalهای دارای Alignment کامل
- تعداد Revisionهای پس از اجرا

## یادگیری مدرس
- کاهش خطاهای تکراری در طرح‌های بعدی
- کاهش نیاز به Guidance در طول زمان
- بهبود توانایی تشخیص نقص طرح بدون AI

## AI
- acceptance/edit/reject ratio
- درصد پیشنهادهای دارای sourceRefs
- خطاهای Hallucination گزارش‌شده

---

# 26. Non-functional Requirements

- RTL-first
- Responsive
- Keyboard accessible
- touch targets مناسب
- prefers-reduced-motion
- deterministic validation
- schema migrations
- unit tests
- contract tests
- golden tests
- E2E
- CI build verification
- no hidden network dependency
- clear version reporting

---

# 27. نسخه‌بندی

سه سطح مستقل نسخه دارند:

```
Master Specification
SDK / Engine
Principle Pack
```

نمونه:
```
Master 0.1
SDK 0.1
LD17 1.0
```

Project Manifest باید نسخه‌های استفاده‌شده را ثبت کند.

---

# 28. ارتباط با kelas-zende

`kelas-zende` الگوی مفیدی برای:
- Source → Engine → Build → Artifact
- Stable ID
- Manifest
- Bridge
- Event Model
- Offline runtime
- Tests/CI

است.

LDX نباید Domain خود را به `LESSON + slides` تقلیل دهد. ارتباط مطلوب:

```
LDX Lesson Designer
        ↓
Lesson Plan / Design Model
        ↓
Exporter / Adapter
        ↓
kelas-zende compatible content (optional)
        ↓
Interactive Lesson Runtime
```

پس kelas-zende یک Runtime/Target احتمالی است، نه Domain Model اصلی LDX.

---

# 29. تصمیم‌های باز برای v0.2

این موارد عمداً هنوز قفل نشده‌اند:

1. فهرست دقیق اصول غیرقابل Override
2. نحوه محاسبه Score کلی، یا حذف Score کلی
3. مدل دقیق سطح شناختی Goal
4. OCR آفلاین در Core یا Plugin
5. فرمت package پروژه (.ldxproj)
6. میزان نگهداری فایل اصلی در IndexedDB
7. مدل سازمانی Preset و Policy
8. همگام‌سازی چند دستگاه
9. استاندارد اتصال مستقیم به LLMها
10. Mapping رسمی به kelas-zende
11. مدل Rubric برای حوزه/دانشگاه/مدرسه
12. محدوده دقیق Source Citation در خروجی طرح

---

# 30. قاعده توسعه از این پس

هر قابلیت جدید قبل از ورود به UI باید پاسخ دهد:

1. مسئله‌ای که حل می‌کند چیست؟
2. Entity یا Data مورد نیاز چیست؟
3. Rule یا Decision آن کجاست؟
4. آیا Configurable است یا Core؟
5. Evidence موفقیت چیست؟
6. چه Eventی تولید می‌کند؟
7. چه Testی باید داشته باشد؟
8. آیا Offline کار می‌کند؟
9. AI اگر حذف شود چه بخشی باقی می‌ماند؟
10. آیا توسعه بعدی بدون تغییر Core ممکن است؟

اگر پاسخ این پرسش‌ها روشن نیست، قابلیت هنوز آماده پیاده‌سازی نیست.

---

## جمع‌بندی

LDX باید از «فرم طرح درس» و «مولد متن با AI» عبور کند و به یک **Design Intelligence Platform** تبدیل شود: سامانه‌ای که تصمیم‌های آموزشی را ساختاریافته می‌کند، شواهد می‌خواهد، روابط را می‌سنجد، توصیه می‌کند، ولی قضاوت نهایی را نزد مدرس نگه می‌دارد.

Master منبع حقیقت این منطق است؛ SDK آن را اجرا می‌کند؛ و هر App فقط یک تجلی از این هسته است.
