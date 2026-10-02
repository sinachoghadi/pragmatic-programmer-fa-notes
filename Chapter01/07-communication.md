# درس 07 — Communicate!
## ارتباط حرفه‌ای در مهندسی نرم‌افزار

داشتن بهترین ایده یا بهترین کد کافی نیست.

باید بتوانی:

- مشکل را توضیح بدهی
- تصمیم را دفاع کنی
- Risk را منتقل کنی
- Feedback بگیری
- مستند کنی
- با مخاطب‌های مختلف صحبت کنی

---

# 1. Know Your Audience

یک مفهوم را برای همه یکسان توضیح نده.

فرض کن می‌خواهی Caching اضافه کنی.

### Developer

> Requestهای تکراری کم می‌شوند و Latency پایین‌تر می‌آید.

### PM

> صفحه سریع‌تر باز می‌شود و کاربر کمتر منتظر می‌ماند.

### Engineering Manager

> Load روی Backend کمتر می‌شود و Scalability بهتر می‌شود.

یک مفهوم، سه مدل بیان.

---

# 2. Know What You Want to Say

قبل از جلسه یا پیام، ساختار داشته باش.

بد:

> Dashboard کلاً مشکل داره، useEffect زیاده، API هم بده...

بهتر:

```text
Problem:
Dashboard کند است.

Evidence:
Initial load ≈ 4.5s

Cause:
سه Request به‌صورت Sequential اجرا می‌شوند.

Proposal:
دو Request را Parallel کنیم و یکی را Cache کنیم.

Impact:
Load Time کمتر می‌شود.
```

---

# 3. Choose Your Moment

زمان درست بخشی از Communication است.

وسط Production Incident زمان خوبی برای پیشنهاد مهاجرت State Management نیست.

اول:

```text
Restore
↓
Stabilize
↓
Investigate
↓
Improve
```

---

# 4. Choose Your Style

برای Developer:

> Race Condition بین Refresh Token و Requestهای Parallel داریم.

برای فرد غیر فنی:

> وقتی چند درخواست هم‌زمان ارسال می‌شود، سیستم گاهی وضعیت ورود را اشتباه تشخیص می‌دهد.

محتوا یکی است؛ سطح جزئیات فرق می‌کند.

---

# 5. Code Review Communication

کامنت ضعیف:

> any نذار.

کامنت بهتر:

> بهتره Response تایپ مشخص داشته باشه، چون با `any` اگر Shape پاسخ API تغییر کنه TypeScript نمی‌تونه خطا رو زود تشخیص بده.

مثلاً:

```ts
type UserResponse = {
  id: number;
  name: string;
};

const data: UserResponse = await response.json();
```

Review خوب فقط دستور نمی‌دهد؛ دلیل هم می‌دهد.

---

# 6. Be a Listener

PM:

> این صفحه باید سریع‌تر بشه.

Developer ضعیف:

> Lazy Loading می‌زنیم.

Developer بهتر:

> منظورت Initial Load هست یا سرعت Interaction بعد از Load؟

قبل از Solution، Problem را درست بفهم.

---

# 7. Follow Up

سکوت اعتماد را کاهش می‌دهد.

اگر پاسخ کامل نداری، Status بده:

> هنوز Root Cause را پیدا نکردم، ولی بررسی اولیه نشان می‌دهد احتمالاً مشکل مربوط به Refresh Token است. قدم بعدی Network Flow را بررسی می‌کنم.

---

# 8. Documentation

Documentation نباید کاری باشد که آخر پروژه «اگر وقت شد» انجام دهی.

باید تا حد ممکن بخشی از Development باشد.

اما هر خط کد نیاز به Comment ندارد.

بد:

```ts
// increment counter by one
counter++;
```

خوب:

```ts
// We intentionally avoid retrying this request
// because the endpoint is not idempotent.
```

اصل مهم:

```text
Code → HOW
Comment → WHY
```

---

## مثال

بد:

```ts
// check if user is admin
if (user.role === "admin") {
  // ...
}
```

بهتر:

```ts
// Admins bypass this check because legacy accounts
// don't have explicit permissions yet.
if (user.role === "admin") {
  // ...
}
```

---

# مدل ذهنی Communication

```text
چه می‌خواهم بگویم؟
 ↓
به چه کسی؟
 ↓
چقدر Technical؟
 ↓
الان زمان مناسبی است؟
 ↓
آیا فهمیده شد؟
 ↓
آیا Feedback گرفتم؟
 ↓
آیا Follow-up لازم است؟
```

---

# مثال نهایی: تأخیر Feature

واقعیت:

- API یک روز دیر آمده.
- Estimation تو هم کمتر از Complexity واقعی بوده.
- Feature حدود ۹۰٪ آماده است.

پاسخ حرفه‌ای:

> API یک روز دیرتر آماده شد و من هم پیچیدگی بخش Validation را کمتر از مقدار واقعی برآورد کردم. الان حدود ۹۰٪ Feature آماده است. برای اینکه Release بقیه بخش‌ها متوقف نشود، Feature را پشت Feature Flag نگه می‌دارم و تا زمان آماده شدن API با Mock توسعه و تست را ادامه می‌دهم. بخش‌های Polish غیرضروری را هم به Iteration بعد منتقل می‌کنم. بعد از اتصال API، Flow نهایی را Integration Test می‌کنیم و Feature را فعال می‌کنیم.

این پاسخ شامل:

- Responsibility
- Transparency
- Options
- Risk Management
- Good Enough Software
- Clear Communication

است.
