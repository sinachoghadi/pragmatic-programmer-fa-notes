# The Pragmatic Programmer — Study Notes

مجموعه‌ی یادداشت‌ها و درسنامه‌های شخصی من از کتاب **The Pragmatic Programmer** با تمرکز بر درک عملی مفاهیم مهندسی نرم‌افزار.

هدف این Repository صرفاً خلاصه‌کردن کتاب نیست. سعی می‌کنم هر مفهوم را به زبان ساده یاد بگیرم و بعد آن را با مثال‌های واقعی، مخصوصاً با **React و TypeScript**، به دنیای توسعه نرم‌افزار وصل کنم.

> این Repository یادداشت‌ها و برداشت‌های آموزشی شخصی من است و جایگزین نسخه اصلی کتاب نیست.  
> این پروژه هیچ وابستگی رسمی به نویسندگان یا ناشر کتاب ندارد.

---

## چرا این Repository را ساختم؟

هنگام مطالعه کتاب نمی‌خواهم فقط مطالب را بخوانم و از آن‌ها عبور کنم.

برای هر موضوع سعی می‌کنم:

- مفهوم اصلی را بفهمم
- آن را به زبان ساده بازنویسی کنم
- کاربرد آن را در پروژه‌های واقعی بررسی کنم
- مثال‌های React و TypeScript بسازم
- Trade-offها را بررسی کنم
- با سناریو و تمرین، خودم را محک بزنم
- نکات مهم را برای مرور آینده نگه دارم

---

# Sections

## ✅ Section 01 — A Pragmatic Philosophy

در این بخش درباره طرز فکر یک **Pragmatic Programmer** و نحوه برخورد یک مهندس نرم‌افزار با مسئولیت، کیفیت، تغییر، یادگیری و ارتباط صحبت می‌کنیم.

### Lessons

| # | Lesson | Status |
|---|---|---|
| 01 | [You Have Agency](./Chapter01/01-agency.md) | ✅ |
| 02 | [Take Responsibility — Provide Options](./Chapter01/02-responsibility-and-options.md) | ✅ |
| 03 | [Software Entropy & Broken Windows](./Chapter01/03-software-entropy-broken-windows.md) | ✅ |
| 04 | [Stone Soup & Boiled Frog](./Chapter01/04-stone-soup-and-boiled-frog.md) | ✅ |
| 05 | [Good-Enough Software](./Chapter01/05-good-enough-software.md) | ✅ |
| 06 | [Your Knowledge Portfolio](./Chapter01/06-knowledge-portfolio.md) | ✅ |
| 07 | [Communicate!](./Chapter01/07-communication.md) | ✅ |

---

## مفاهیم اصلی Section 01

در این بخش با مفاهیمی مثل موارد زیر آشنا می‌شویم:

### Agency

وقتی مشکلی می‌بینی فقط نپرس:

> چه کسی مقصر است؟

بپرس:

> چه چیزی در محدوده اختیار من است که می‌توانم بهترش کنم؟

---

### Responsibility

به‌جای بهانه، **گزینه ارائه بده**.

```text
Problem
   ↓
Cause
   ↓
What is under my control?
   ↓
Available options
   ↓
Trade-offs
   ↓
Recommendation
```

---

### Broken Windows

اجازه نده کد ضعیف و تصمیمات بد تبدیل به استاندارد جدید پروژه شوند.

هدف این نیست که هر چیزی را فوراً Refactor کنیم.

هدف این است که:

> خرابی جدید به سیستم اضافه نکنیم و بخشی را که لمس می‌کنیم، در صورت امکان کمی بهتر تحویل بدهیم.

---

### High Cohesion + Low Coupling

سعی می‌کنیم چیزهایی که متعلق به یک Feature هستند کنار هم باشند و Featureها تا حد امکان وابستگی کمی به جزئیات داخلی یکدیگر داشته باشند.

```text
features/
  payments/
    components/
    hooks/
    services/
    types/
```

---

### Remember the Big Picture

مشکلات نرم‌افزار همیشه ناگهانی ایجاد نمی‌شوند.

گاهی:

```text
250 lines
↓
350
↓
500
↓
800
↓
1200
```

و هیچ لحظه مشخصی وجود ندارد که بتوان گفت:

> امروز Architecture خراب شد.

به همین دلیل علاوه بر Task فعلی باید جهت کلی سیستم را هم ببینیم.

---

### Good-Enough Software

هدف ساختن نرم‌افزار بی‌کیفیت نیست.

هدف پیدا کردن تعادل بین این موارد است:

```text
Quality
Time
Scope
Cost
Risk
User Value
```

و تشخیص اینکه:

> چه چیزی Release Blocker است و چه چیزی می‌تواند برای Iteration بعدی منتظر بماند؟

---

### Knowledge Portfolio

دانش را مثل یک سرمایه‌گذاری مدیریت می‌کنیم.

```text
Regular Investment
+
Diversification
+
Risk Management
+
Rebalancing
+
Critical Thinking
```

فقط Tool یاد نمی‌گیریم؛ سعی می‌کنیم Conceptهای زیر آن را هم بفهمیم.

---

### Communication

مهندس خوب فقط کد خوب نمی‌نویسد.

باید بتواند:

- مسئله را واضح توضیح دهد
- Evidence ارائه کند
- Trade-off را توضیح دهد
- پیشنهاد بدهد
- مخاطبش را بشناسد
- Feedback بگیرد
- تصمیمات مهم را مستند کند

یک مدل ساده:

```text
Problem
↓
Evidence
↓
Cause
↓
Options
↓
Recommendation
↓
Impact
```

---

# رویکرد آموزشی

برای هر درس سعی می‌کنم تقریباً این مسیر را طی کنم:

```text
Concept
   ↓
Simple Explanation
   ↓
Real-world Scenario
   ↓
React / TypeScript Example
   ↓
Common Mistakes
   ↓
Trade-offs
   ↓
Exercise
```

هدف این است که مفاهیم فقط حفظ نشوند، بلکه بتوانم آن‌ها را در:

- پروژه واقعی
- Code Review
- تصمیم‌های معماری
- Debugging
- مصاحبه فنی
- همکاری تیمی

استفاده کنم.

---

# Tech Focus

مثال‌های فنی این Repository بیشتر حول این تکنولوژی‌ها هستند:

- React
- TypeScript
- Next.js
- JavaScript
- Front-end Architecture
- Testing
- Web APIs
- Software Engineering

با این حال، مفاهیم اصلی کتاب وابسته به Framework خاصی نیستند.

---

# Repository Structure

در حال حاضر ساختار Repository به این صورت است:

```text
.
├── README.md
│
└── 01/
    ├── 01-agency.md
    ├── 02-responsibility-and-options.md
    ├── 03-software-entropy-broken-windows.md
    ├── 04-stone-soup-and-boiled-frog.md
    ├── 05-good-enough-software.md
    ├── 06-knowledge-portfolio.md
    └── 07-communication.md
```

با ادامه مطالعه، Sectionهای جدید به همین ساختار اضافه خواهند شد.

---

# Progress

```text
Section 01  ██████████  100%
```

- [x] Section 01 — A Pragmatic Philosophy
- [ ] Section 02
- [ ] Section 03
- [ ] Section 04
- [ ] سایر بخش‌ها...

این Repository به‌مرور و همزمان با مطالعه کتاب تکمیل می‌شود.

---

# Disclaimer

**The Pragmatic Programmer** اثر **David Thomas** و **Andrew Hunt** است.

حقوق کتاب، متن اصلی و محتوای رسمی آن متعلق به نویسندگان و صاحبان حقوق مربوطه است.

محتوای این Repository شامل یادداشت‌ها، توضیحات، مثال‌ها، تمرین‌ها و برداشت‌های آموزشی شخصی است و با هدف مطالعه و یادگیری تهیه شده است.

برای مطالعه کامل مطالب، از نسخه رسمی کتاب استفاده کنید.