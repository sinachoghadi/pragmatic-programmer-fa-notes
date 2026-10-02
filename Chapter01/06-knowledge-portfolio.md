# درس 06 — Your Knowledge Portfolio
## سبد دانش

دانش حرفه‌ای یک دارایی است، اما ارزش آن می‌تواند با زمان کاهش پیدا کند.

پس یادگیری باید یک فعالیت اتفاقی نباشد؛ باید آن را مثل سرمایه‌گذاری مدیریت کنی.

---

# 1. Regular Investment

یادگیری منظم از مطالعه سنگین و پراکنده بهتر است.

بد:

```text
جمعه:
8 ساعت TypeScript

بعد:
3 هفته هیچ‌چیز
```

بهتر:

```text
هر روز:
30 تا 45 دقیقه
```

مثلاً:

```text
روز 1 → Union Types
روز 2 → Generics
روز 3 → keyof
روز 4 → Utility Types
روز 5 → Practice
```

---

# 2. Diversification

اگر فقط React بلد باشی، سبدت ریسک بالایی دارد.

سبد بهتر:

```text
Frontend
├── React
├── TypeScript
├── Browser Internals
├── Performance
└── Accessibility

Backend Concepts
├── HTTP
├── REST
├── Authentication
└── Database Basics

Engineering
├── Testing
├── Git
├── Architecture
└── CI/CD
```

هدف این نیست که در همه‌چیز Expert شوی.

هدف این است که دیدت محدود به یک Tool نباشد.

---

# 3. Risk Management

ترکیبی از دانش Stable و Experimental داشته باش.

مثلاً:

```text
Low Risk:
TypeScript
React
HTTP
SQL

Medium Risk:
Next.js جدید
Server Components

Higher Risk:
Framework تازه با Adoption کم
```

تمام وقتت را روی Hype نگذار، ولی کاملاً هم از فناوری‌های جدید دور نمان.

---

# 4. Buy Low, Sell High

گاهی یادگیری یک Technology قبل از فراگیر شدن ارزش بالایی ایجاد می‌کند.

اما هر Technology جدیدی ارزش سرمایه‌گذاری ندارد.

بپرس:

- مسئله واقعی حل می‌کند؟
- Adoption دارد رشد می‌کند؟
- Conceptهایش قابل انتقال‌اند؟

---

# 5. Rebalance

سبد دانش باید تغییر کند.

مثلاً قبلاً:

```text
React      ██████████
JavaScript █████████
CSS        ███████
TypeScript ██
Testing    █
```

بعداً ممکن است نیاز داشته باشی:

```text
React         ███████
TypeScript    ███████
Testing       █████
Next.js       █████
Architecture  ████
```

---

## برنامه‌ای که برای خودمان انتخاب کردیم

با توجه به ضعف نسبی و نیاز بازار:

```text
TypeScript → 1 ساعت
Testing    → 2 ساعت
Next.js    → 2 ساعت
```

اما این برنامه دائمی نیست.

بعد از چند هفته باید Rebalance شود.

مثلاً:

```text
TypeScript     → 1h
Next.js        → 1.5h
Testing        → 1h
System Design  → 1.5h
```

---

# Critical Thinking

فقط زیاد مطالعه کردن کافی نیست.

نباید هر ادعای فنی را بدون سؤال بپذیری.

مثلاً:

> Redux is dead.

سؤال‌های بهتر:

- چه کسی گفته؟
- برای چه نوع پروژه‌ای؟
- Context چیست؟
- Trade-off چیست؟
- Redux چه زمانی بهتر است؟
- Zustand چه زمانی بهتر است؟

---

# Five Whys

مثال:

> صفحه کند است.

چرا؟

> Render زیاد داریم.

چرا؟

> State زیاد Update می‌شود.

چرا؟

> WebSocket هر ثانیه Store را Update می‌کند.

چرا؟

> کل Payload در Global State قرار می‌گیرد.

در این نقطه دیگر مسئله فقط «React کند است» نیست.

ممکن است مشکل Data Architecture باشد.

---

## مثال useMemo

ادعا:

> همه‌جا useMemo استفاده کنیم تا Performance بهتر شود.

تفکر نقادانه:

- Computation واقعاً گران است؟
- Reference Stability لازم داریم؟
- Profiling کرده‌ایم؟
- هزینه Memoization چقدر است؟

گاهی:

```tsx
const value = a + b;
```

بهتر از این است:

```tsx
const value = useMemo(() => a + b, [a, b]);
```

---

## تمرین دوره‌ای

هر ماه از خودت بپرس:

1. کدام Skill بیش از حد سهم گرفته؟
2. کدام Skill عقب مانده؟
3. بازار یا پروژه‌های من چه چیزی می‌خواهند؟
4. کدام Concept پایه‌ای را باید عمیق‌تر کنم؟
5. آیا دارم فقط Tool یاد می‌گیرم یا Concept هم یاد می‌گیرم؟
