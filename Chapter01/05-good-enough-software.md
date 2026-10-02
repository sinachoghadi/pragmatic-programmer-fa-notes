# درس 05 — Good-Enough Software
## نرم‌افزار به‌اندازه کافی خوب

Good Enough به معنی «کد بد» نیست.

یعنی کیفیت را با این عوامل کنار هم ببینی:

```text
Quality
Time
Cost
Scope
Risk
User Value
```

---

## مثال

دو نسخه داری.

### نسخه اول

```text
- Feature اصلی کار می‌کند
- Validation دارد
- Error Handling دارد
- تست‌های Critical دارد
- UI شاید کاملاً Polish نشده
```

### نسخه دوم

```text
- Animation عالی
- Architecture کاملاً Refactor
- Edge Caseهای نادر پوشش داده شده
- Naming همه‌جا Perfect
- Release سه هفته عقب افتاده
```

در خیلی از شرایط نسخه اول تصمیم حرفه‌ای‌تری است.

---

# Quality باید Requirement باشد

همان‌طور که می‌پرسی:

> Feature چه کاری انجام دهد؟

باید بپرسی:

- چقدر Reliable؟
- چقدر Fast؟
- چقدر Secure؟
- چقدر Polished؟

مثلاً:

```text
Search باید زیر 200ms باشد.
```

یا:

```text
Payment نباید Duplicate Transaction ایجاد کند.
```

این‌ها Quality Requirement هستند.

---

## Context مهم است

Quality یک عدد ثابت نیست.

```text
Landing Page
→ Visual Quality مهم‌تر

Internal Admin Tool
→ Reliability و Efficiency مهم‌تر

Banking
→ Correctness + Security بسیار مهم

Prototype
→ Learning Speed مهم‌تر
```

---

# Know When to Stop

یکی از خطرهای برنامه‌نویسی:

> Over-engineering

مثلاً این کافی است:

```ts
function calculateTotal(items: CartItem[]): number {
  return items.reduce(
    (total, item) =>
      total + item.price * item.quantity,
    0
  );
}
```

اما شروع می‌کنی:

- Generic
- Strategy Pattern
- Factory
- Dependency Injection
- Abstraction Layer

برای یک `reduce` ساده.

سؤال پراگماتیک:

> آیا مشکل واقعی حل می‌کنم یا Complexity تولید می‌کنم؟

---

# Good Enough vs Bad Software

## Good Enough

```text
✓ نیاز کاربر را برآورده می‌کند
✓ Critical Test دارد
✓ Maintainable است
✓ Risk قابل قبول دارد
✓ در زمان مناسب تحویل می‌شود
```

## Bad Software

```text
✗ Error Handling ندارد
✗ Security Problem دارد
✗ کد ناخواناست
✗ Bug حیاتی شناخته‌شده دارد
✗ صرفاً برای Release سریع نوشته شده
```

---

## Release Blocker چیست؟

فرض کن Checkout داری:

```text
1. Payment
2. Validation
3. Loading
4. Error Handling
5. Duplicate-submit protection
6. Critical tests
7. Animation
8. Dark Mode
9. Keyboard Shortcuts
10. Full Refactor
```

ممکن است تصمیم بگیری:

```text
Release Blockers:
1 تا 6

Can Wait:
7 تا 10
```

---

## مثال Search Page

الان:

```text
✓ Search
✓ Loading
✓ Error State
✓ TypeScript
✓ Main Test
✓ Response ≈ 400ms
```

ولی:

```text
× Debounce
× Skeleton
× Recent Searches
× Keyboard Navigation
× Caching
```

Debounce فقط وقتی Release Blocker است که نبودش Risk واقعی ایجاد کند:

- API Load بالا
- Rate Limit
- Cost
- UX بد

اگر این Risk وجود ندارد، ممکن است Release بدون آن منطقی باشد.

---

## پنج سؤال قبل از Polish بیشتر

1. Requirement اصلی کامل شده؟
2. Risk Critical باقی مانده؟
3. این تغییر User Value واقعی ایجاد می‌کند؟
4. هزینه این Polish ارزشش را دارد؟
5. اگر الان Release کنیم چه چیز مهمی خراب می‌شود؟

اگر پاسخ سؤال پنجم «چیز مهمی نیست» باشد، احتمالاً وقت Release است.
