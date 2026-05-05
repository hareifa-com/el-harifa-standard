# كيف تساهم | Contributing

> **"المعيار ده بتاعنا كلنا. مش بتاعي أنا لوحدي."**

---

## شكراً ليك

إنك بتفكر تساهم في معيار الحريفة. ده معناه إنك مش مجرد متفرج. إنت جزء من الحل.

السطور دي هتشرحلك إزاي تساهم في المستودع ده. العملية بسيطة. متقلقش.

---

## قواعد الاشتباك

### 1. تمهل
قبل ما تكتب أي حاجة، نزل الإصدار الأخير من المستودع:
```bash
git pull origin main

2. اعمل Branch منفصل

ابدأ دايماً من main. لكن متشتغلش على main مباشرة.
bash

git checkout -b feat/your-feature-name

أو:
bash

git checkout -b fix/your-fix-name

3. اكتب Commit مفهومة

الـ Commit message لازم تكون واضحة ومفيدة.

    : docs: add goalkeeper evaluation examples

    : feat: add glossary for technical terms

    : fix: correct scoring scale description

    : schema: add player profile JSON schema

4. اشرح تعديلك

في وصف الـ Pull Request، جاوب على الأسئلة دي:

    ليه التعديل ده ضروري؟

    إيه اللي اتغير بالضبط؟

    هل الكلام ده اتناقش في Issue قبل كده؟ (لو فيه، اربطه)

أنواع المساهمات
النوع الأول: تعديل على الوثائق

    تحسين شرح. توضيح غامض. إضافة أمثلة.

    عدل الملف مباشرة وافتح PR.

النوع الثاني: تعديل على المعيار

    تغيير في المقياس. إضافة معيار جديد. تعديل الحوكمة.

    الضروري: افتح Issue أولاً للنقاش قبل ما تكتب كود. التغييرات الكبيرة لازم المجتمع يشوفها.

النوع الثالث: إضافة سكيما (JSON Schema)

    إضافة أو تعديل ملفات schemas/.

    تأكد إن شغلك متوافق مع JSON Schema Draft 2020-12.

    اختبر السكيما قبل الرفع.

النوع الرابع: ترجمة

    ترجمة الوثائق للغات أخرى (إنجليزي، فرنسي).

    ضع الملفات في مجلد translations/.

دورة حياة المساهمة

    شوف الـ Issues: لو في Issue مفتوح، شوف إذا كنت تقدر تساعد.

    لو لقيت مشكلة مش مذكورة: افتح Issue جديد. اشرح المشكلة أو الاقتراح.

    ناقش: المجتمع (أنا والمشرفين) هيردوا عليك. نقاش مفتوح.

    اكتب الكود/التعديل: اعمل Branch، عدل، Commit.

    افتح Pull Request: اربطه بـ Issue.

    مراجعة: أنا أو حد تاني هيراجع شغلك.

    دمج: لو كل شيء تمام، الـ PR يتدمج في main.

    احتفل: اسمك هيظهر في المساهمين.

احتياجات عاجلة

الحاجات دي مستنية مساهمتك:

    إضافة أمثلة حقيقية لتقييمات في كل مركز (GK, CB, ST...).

    تحسين شرح مقياس 1-10 بأمثلة فيديو.

    ترجمة SCOUTING_GUIDE.md للإنجليزية.

    إضافة SCHEMA.md كامل.

    إنشاء ملفات schemas/ للتحقق التلقائي من البيانات.

    كتابة اختبارات للـ JSON Schema.

تواصل معايا

لو عندك سؤال، افتح Issue. لو عايز تتكلم مباشر، ابعت لي على:

    GitHub: @izzeldeenn

    البريد: [soon]

    "مافيش حاجة اسمها مساهمة صغيرة. كل كلمة بتضيفها بتبني المعيار."

text


---

## ثالثاً: `SCHEMA.md`

```markdown
# هيكل البيانات | Data Schema

> **"البيانات الفوضوية بتضيع المواهب. البيانات المنظمة بتكتشفها."**

---

## ما هذا؟

هذا الملف يشرح هيكل البيانات الرسمي لمعيار الحريفة.

كل لاعب، كل تقييم، كل أكاديمية، كل مستخدم يتم تمثيله رقمياً حسب هذه الهياكل. الهدف هو ضمان أن أي نظام (منصتنا، أو أي نظام خارجي) يمكنه قراءة وكتابة بيانات متوافقة.

---

## الكيانات الرئيسية

### 1. اللاعب (Player)
القلب النابض للمشروع.

| الحقل | النوع | مطلوب | الوصف |
|:---|:---|:---|:---|
| `id` | UUID | نعم | معرف فريد |
| `full_name_ar` | string | نعم | الاسم الثلاثي بالعربية |
| `birth_date` | date (YYYY-MM-DD) | نعم | تاريخ الميلاد |
| `birth_place` | string | لا | مكان الميلاد (قرية، مدينة) |
| `governorate` | GovernorateCode | نعم | المحافظة (كود من قائمة المحافظات) |
| `academy_id` | UUID | لا | الأكاديمية (إن وجدت) |
| `height_cm` | number | لا | الطول بالسنتيمتر |
| `weight_kg` | number | لا | الوزن بالكيلوجرام |
| `dominant_foot` | "right" \| "left" \| "both" | نعم | القدم المفضلة |
| `primary_position` | PositionCode | نعم | المركز الأساسي |
| `secondary_position` | PositionCode | لا | المركز الثانوي |
| `bio` | string | لا | نبذة عن اللاعب |
| `family_status` | string | لا | حالة الأسرة (اختياري، لتحديد الاحتياجات) |
| `daily_travel_to_training` | string | لا | وقت/مسافة الوصول للتمرين |
| `school_performance` | string | لا | وصف الأداء الأكاديمي |
| `scout_story` | string | لا | قصة الاكتشاف |
| `latitude` | number | لا | خط العرض (GPS) |
| `longitude` | number | لا | خط الطول (GPS) |
| `status` | "active" \| "incomplete" \| "archived" | نعم | حالة اللاعب |
| `created_by` | UUID | نعم | معرف المستخدم الذي أضاف اللاعب |
| `created_at` | timestamp | نعم | وقت الإضافة |
| `updated_at` | timestamp | نعم | وقت آخر تحديث |

---

### 2. التقييم (Evaluation)

| الحقل | النوع | مطلوب | الوصف |
|:---|:---|:---|:---|
| `id` | UUID | نعم | معرف فريد |
| `player_id` | UUID | نعم | معرف اللاعب |
| `evaluator_id` | UUID | نعم | معرف المقيم |
| `evaluator_role` | "مدرب" \| "كشاف" \| "متطوع" | نعم | دور المقيم |
| `evaluation_type` | "مدرب" \| "كشاف" \| "متطوع" | نعم | نوع التقييم |
| `event_name` | string | لا | اسم البطولة أو المباراة |
| `event_date` | date | لا | تاريخ المباراة |
| `minutes_watched` | number | لا | كم دقيقة مشاهدة |
| `technical_skills` | TechnicalSkills | نعم | المهارات التقنية (كلها 1-10) |
| `physical_attributes` | PhysicalAttributes | نعم | القدرات البدنية (كلها 1-10) |
| `mental_attributes` | MentalAttributes | نعم | المهارات الذهنية (كلها 1-10) |
| `commitment` | Commitment | نعم | الالتزام (كلها 1-10) |
| `overall_potential` | "A" \| "B" \| "C" \| "D" | نعم | الإمكانات العامة |
| `strengths` | string | لا | نقاط القوة |
| `weaknesses` | string | لا | نقاط الضعف |
| `scout_notes` | string | لا | ملاحظات حرة |
| `video_url` | string | لا | رابط فيديو |
| `weight` | 1 \| 2 \| 3 | نعم | وزن التقييم (1:مدرب, 2:أكاديمية, 3:كشاف) |
| `status` | "معتمد" \| "قيد_المراجعة" \| "مرفوض" | نعم | حالة التقييم |
| `created_at` | timestamp | نعم | وقت التقييم |

---

### 3. الأكاديمية (Academy)

| الحقل | النوع | مطلوب | الوصف |
|:---|:---|:---|:---|
| `id` | UUID | نعم | معرف فريد |
| `name_ar` | string | نعم | اسم الأكاديمية |
| `governorate` | GovernorateCode | نعم | المحافظة |
| `type` | "مركز_شباب" \| "اكاديمية" \| "نادي" \| "مدرسة" | نعم | النوع |
| `address` | string | لا | العنوان |
| `latitude` | number | لا | خط العرض |
| `longitude` | number | لا | خط الطول |
| `coach_name` | string | لا | اسم المدرب الرئيسي |
| `coach_phone` | string | لا | هاتف المدرب |
| `manager_id` | UUID | نعم | معرف مدير الأكاديمية |
| `status` | "نشط" \| "قيد_المراجعة" \| "موقوف" \| "مرفوض" | نعم | حالة الأكاديمية |
| `created_at` | timestamp | نعم | وقت التسجيل |

---

### 4. المستخدم (User)

| الحقل | النوع | مطلوب | الوصف |
|:---|:---|:---|:---|
| `id` | UUID | نعم | معرف فريد |
| `full_name` | string | نعم | الاسم |
| `phone` | string | لا | الهاتف |
| `email` | string | لا | البريد |
| `role` | "مدرب" \| "كشاف" \| "متطوع" \| "admin" \| "regional_admin" | نعم | الدور |
| `governorate` | GovernorateCode | لا | المحافظة |
| `academy_id` | UUID | لا | الأكاديمية التابع لها |
| `verified` | boolean | نعم | هل هو معتمد؟ |
| `created_at` | timestamp | نعم | وقت التسجيل |

---

## الأنواع المخصصة (Custom Types)

### TechnicalSkills
```json
{
  "dribbling": "number (1-10)",
  "first_touch": "number (1-10)",
  "passing_short": "number (1-10)",
  "passing_long": "number (1-10)",
  "shooting": "number (1-10)",
  "tackling": "number (1-10)"
}

PhysicalAttributes
json

{
  "pace": "number (1-10)",
  "stamina": "number (1-10)",
  "strength": "number (1-10)",
  "agility": "number (1-10)"
}

MentalAttributes
json

{
  "decision_making": "number (1-10)",
  "vision": "number (1-10)",
  "composure": "number (1-10)",
  "leadership": "number (1-10)"
}

Commitment
json

{
  "training_attendance": "number (1-10)",
  "academic_discipline": "number (1-10)",
  "coachability": "number (1-10)"
}

أمثلة
مثال لاعب كامل:

انظر الملف: examples/player-example.json
مثال تقييم كامل:

انظر الملف: examples/evaluation-example.json
التحقق من صحة البيانات

لمن يريد التحقق من صحة JSON ضد هذه الهياكل، ملفات JSON Schema موجودة في مجلد schemas/.

استخدم:

    schemas/player.schema.json

    schemas/evaluation.schema.json

    "القاعدة: لو في شك، ارجع لـ Schema. SCHEMA هو الحَكَم."

text


---

## رابعاً: مجلد `schemas/` بملفّيه

### `schemas/player.schema.json`

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://hareifa.com/schemas/player.schema.json",
  "title": "لاعب",
  "description": "هيكل بيانات لاعب كرة قدم ناشئ في معيار الحريفة",
  "type": "object",
  "required": [
    "id",
    "full_name_ar",
    "birth_date",
    "governorate",
    "dominant_foot",
    "primary_position",
    "status",
    "created_by"
  ],
  "properties": {
    "id": {
      "type": "string",
      "format": "uuid",
      "description": "معرف فريد للاعب"
    },
    "full_name_ar": {
      "type": "string",
      "minLength": 6,
      "maxLength": 100,
      "description": "الاسم الثلاثي بالعربية"
    },
    "birth_date": {
      "type": "string",
      "format": "date",
      "description": "تاريخ الميلاد YYYY-MM-DD"
    },
    "birth_place": {
      "type": "string",
      "maxLength": 100,
      "description": "مكان الميلاد"
    },
    "governorate": {
      "type": "string",
      "enum": [
        "القاهرة", "الإسكندرية", "الجيزة", "القليوبية", "المنوفية",
        "الغربية", "كفر_الشيخ", "البحيرة", "دمياط", "الدقهلية",
        "الشرقية", "الإسماعيلية", "بور_سعيد", "السويس", "شمال_سيناء",
        "جنوب_سيناء", "الفيوم", "بني_سويف", "المنيا", "أسيوط",
        "سوهاج", "قنا", "الأقصر", "أسوان", "الوادي_الجديد",
        "البحر_الأحمر", "مطروح"
      ],
      "description": "المحافظة"
    },
    "academy_id": {
      "type": "string",
      "format": "uuid",
      "description": "معرف الأكاديمية (إن وجدت)"
    },
    "height_cm": {
      "type": "number",
      "minimum": 100,
      "maximum": 220,
      "description": "الطول بالسنتيمتر"
    },
    "weight_kg": {
      "type": "number",
      "minimum": 25,
      "maximum": 150,
      "description": "الوزن بالكيلوجرام"
    },
    "dominant_foot": {
      "type": "string",
      "enum": ["right", "left", "both"],
      "description": "القدم المفضلة"
    },
    "primary_position": {
      "type": "string",
      "enum": ["GK", "CB", "LB", "RB", "CM", "AM", "LW", "RW", "ST"],
      "description": "المركز الأساسي"
    },
    "secondary_position": {
      "type": "string",
      "enum": ["GK", "CB", "LB", "RB", "CM", "AM", "LW", "RW", "ST"],
      "description": "المركز الثانوي"
    },
    "bio": {
      "type": "string",
      "maxLength": 1000,
      "description": "نبذة عن اللاعب"
    },
    "family_status": {
      "type": "string",
      "maxLength": 500,
      "description": "حالة الأسرة"
    },
    "daily_travel_to_training": {
      "type": "string",
      "maxLength": 200,
      "description": "وقت أو مسافة الوصول للتمرين"
    },
    "school_performance": {
      "type": "string",
      "maxLength": 200,
      "description": "وصف الأداء الأكاديمي"
    },
    "scout_story": {
      "type": "string",
      "maxLength": 1000,
      "description": "قصة الاكتشاف"
    },
    "latitude": {
      "type": "number",
      "minimum": 22.0,
      "maximum": 31.5,
      "description": "خط العرض (GPS)"
    },
    "longitude": {
      "type": "number",
      "minimum": 25.0,
      "maximum": 35.0,
      "description": "خط الطول (GPS)"
    },
    "status": {
      "type": "string",
      "enum": ["active", "incomplete", "archived"],
      "description": "حالة اللاعب"
    },
    "created_by": {
      "type": "string",
      "format": "uuid",
      "description": "معرف المستخدم الذي أضاف اللاعب"
    },
    "created_at": {
      "type": "string",
      "format": "date-time",
      "description": "وقت الإضافة"
    },
    "updated_at": {
      "type": "string",
      "format": "date-time",
      "description": "وقت آخر تحديث"
    }
  }
}

schemas/evaluation.schema.json
json

{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://hareifa.com/schemas/evaluation.schema.json",
  "title": "تقييم",
  "description": "هيكل تقييم لاعب كرة قدم ناشئ في معيار الحريفة",
  "type": "object",
  "required": [
    "id",
    "player_id",
    "evaluator_id",
    "evaluator_role",
    "technical_skills",
    "physical_attributes",
    "mental_attributes",
    "commitment",
    "overall_potential",
    "weight",
    "status"
  ],
  "properties": {
    "id": {
      "type": "string",
      "format": "uuid"
    },
    "player_id": {
      "type": "string",
      "format": "uuid"
    },
    "evaluator_id": {
      "type": "string",
      "format": "uuid"
    },
    "evaluator_role": {
      "type": "string",
      "enum": ["مدرب", "كشاف", "متطوع"]
    },
    "evaluation_type": {
      "type": "string",
      "enum": ["مدرب", "كشاف", "متطوع"]
    },
    "event_name": {
      "type": "string",
      "maxLength": 150
    },
    "event_date": {
      "type": "string",
      "format": "date"
    },
    "minutes_watched": {
      "type": "integer",
      "minimum": 1,
      "maximum": 120
    },
    "technical_skills": {
      "type": "object",
      "required": ["dribbling", "first_touch", "passing_short", "passing_long", "shooting", "tackling"],
      "properties": {
        "dribbling": { "type": "integer", "minimum": 1, "maximum": 10 },
        "first_touch": { "type": "integer", "minimum": 1, "maximum": 10 },
        "passing_short": { "type": "integer", "minimum": 1, "maximum": 10 },
        "passing_long": { "type": "integer", "minimum": 1, "maximum": 10 },
        "shooting": { "type": "integer", "minimum": 1, "maximum": 10 },
        "tackling": { "type": "integer", "minimum": 1, "maximum": 10 }
      }
    },
    "physical_attributes": {
      "type": "object",
      "required": ["pace", "stamina", "strength", "agility"],
      "properties": {
        "pace": { "type": "integer", "minimum": 1, "maximum": 10 },
        "stamina": { "type": "integer", "minimum": 1, "maximum": 10 },
        "strength": { "type": "integer", "minimum": 1, "maximum": 10 },
        "agility": { "type": "integer", "minimum": 1, "maximum": 10 }
      }
    },
    "mental_attributes": {
      "type": "object",
      "required": ["decision_making", "vision", "composure", "leadership"],
      "properties": {
        "decision_making": { "type": "integer", "minimum": 1, "maximum": 10 },
        "vision": { "type": "integer", "minimum": 1, "maximum": 10 },
        "composure": { "type": "integer", "minimum": 1, "maximum": 10 },
        "leadership": { "type": "integer", "minimum": 1, "maximum": 10 }
      }
    },
    "commitment": {
      "type": "object",
      "required": ["training_attendance", "academic_discipline", "coachability"],
      "properties": {
        "training_attendance": { "type": "integer", "minimum": 1, "maximum": 10 },
        "academic_discipline": { "type": "integer", "minimum": 1, "maximum": 10 },
        "coachability": { "type": "integer", "minimum": 1, "maximum": 10 }
      }
    },
    "overall_potential": {
      "type": "string",
      "enum": ["A", "B", "C", "D"]
    },
    "strengths": {
      "type": "string",
      "maxLength": 500
    },
    "weaknesses": {
      "type": "string",
      "maxLength": 500
    },
    "scout_notes": {
      "type": "string",
      "maxLength": 1000
    },
    "video_url": {
      "type": "string",
      "format": "uri"
    },
    "weight": {
      "type": "integer",
      "enum": [1, 2, 3],
      "description": "1:مدرب, 2:مدير أكاديمية, 3:كشاف معتمد"
    },
    "status": {
      "type": "string",
      "enum": ["معتمد", "قيد_المراجعة", "مرفوض"]
    },
    "reviewed_by": {
      "type": "string",
      "format": "uuid"
    },
    "review_notes": {
      "type": "string",
      "maxLength": 500
    },
    "created_at": {
      "type": "string",
      "format": "date-time"
    }
  }
}

خامساً: مجلد examples/
examples/player-example.json
json

{
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "full_name_ar": "علي محمود عبد الله",
  "birth_date": "2012-05-15",
  "birth_place": "قرية طهنا الجبل، المنيا",
  "governorate": "المنيا",
  "academy_id": null,
  "height_cm": 155.0,
  "weight_kg": 44.0,
  "dominant_foot": "right",
  "primary_position": "CM",
  "secondary_position": "LB",
  "bio": "لاعب وسط موهوب من صعيد مصر. معروف في قريته بقدرته على المراوغة.",
  "family_status": "أسرة بسيطة. الأب فلاح. 3 إخوة.",
  "daily_travel_to_training": "ساعة مشي",
  "school_performance": "متفوق دراسياً رغم الظروف",
  "scout_story": "اكتشفه مدرس التربية الرياضية أثناء اللعب في فناء المدرسة، ثم تواصل معه متطوع من الحريفة.",
  "latitude": 28.1234,
  "longitude": 30.5678,
  "status": "active",
  "created_by": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
  "created_at": "2026-05-05T10:00:00Z",
  "updated_at": "2026-05-05T10:00:00Z"
}
