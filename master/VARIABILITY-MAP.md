# LDX Variability Map v0.1
## نقشه ثابت‌ها، متغیرها و نقاط توسعه

این سند مشخص می‌کند چه چیزهایی باید در توسعه‌های بعدی **تکرارپذیر، قابل تنظیم یا قابل تعویض** باشند تا هر App جدید مجبور به بازنویسی موتور نباشد.

| حوزه | Core / ثابت | Configurable | Plugin / Adapter | App-specific |
|---|---|---|---|---|
| هویت داده | Stable ID, Version | Prefix/label | ID strategy plugin در آینده | نمایش ID |
| Principle | Contract | وزن، سطح، lock | Principle Module | متن آموزشی |
| Rule | Result contract | threshold | Rule plugin | نمایش هشدار |
| Evidence | Evidence schema | required count | Evidence resolver | UI inspector |
| Audit | status model | severity/weights | audit extension | report layout |
| Workflow | graph contract | node order/branches | custom node | wizard/board |
| Audience | profile schema | fields/defaults | domain profile | labels |
| Preset | preset contract | values | preset packs | selector UI |
| Sources | provenance contract | policy | parser/OCR adapters | source viewer |
| AI | proposal contract | provider policy | provider adapters | AI panel |
| Storage | persistence contract | limits | IndexedDB/cloud adapters | settings |
| Export | artifact contract | templates | exporters | export center |
| Events | event envelope | retention | event sinks | analytics UI |
| Revision | immutable history | naming | diff strategy | compare screen |
| Theme | token contract | brand tokens | design-system package | visual identity |
| Integration | bridge envelope | permissions | LMS/kelas adapters | integration UI |

---

## 1. Application Profile

هر محصولی که روی SDK ساخته می‌شود باید یک Application Profile داشته باشد.

نمونه:
```json
{
  "appId": "lesson-designer",
  "title": "LDX Lesson Designer",
  "principlePack": "ld17@1",
  "presetPack": "lesson-defaults@1",
  "workflowPack": "lesson-workflows@1",
  "sourcePolicy": "source-first",
  "aiPolicy": "optional",
  "offlineBaseline": true
}
```

محصول بعدی می‌تواند فقط Application Profile متفاوت داشته باشد:
- course-designer
- assessment-designer
- lesson-auditor
- teacher-reflection
- curriculum-aligner

---

## 2. قابل تغییر بدون تغییر Core

موارد زیر باید از Config خوانده شوند:
- نقش‌ها
- سطوح تجربه مدرس
- مقاطع
- نام Bronze/Silver/Gold
- Principle default levels
- Principle locks
- نوع فیلدهای Context
- Presetها
- ترتیب Workflow
- متن Guidance
- Threshold هشدارها
- قالب خروجی
- Prompt templates
- برند و رنگ
- زبان

---

## 3. نیازمند Plugin

وقتی قابلیت منطق جدیدی وارد می‌کند، به‌جای شرط‌های پراکنده باید Plugin/Adapter باشد:

- اصل جدید
- Parser فایل جدید
- OCR
- LLM جدید
- Export جدید
- Storage جدید
- LMS bridge
- Activity recommender تخصصی
- Rubric تخصصی

---

## 4. ممنوع برای Hard-code در UI

این موارد نباید در Componentهای UI دفن شوند:
- mandatory بودن اصل
- وزن اصل
- تعریف Pass/Fail
- روابط Alignment
- Ruleها
- Source policy
- AI policy
- Workflow branching
- Audit thresholds
- داده Preset

---

## 5. Change Impact

### تغییر کم‌ریسک
- متن
- رنگ
- Label
- default value
- output template

### تغییر متوسط
- preset
- workflow
- principle weight
- threshold
- source policy

### تغییر پرریسک
- schema
- stable IDs
- audit contract
- evidence contract
- event envelope
- revision model

تغییر پرریسک باید Migration و Contract Test داشته باشد.
