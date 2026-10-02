# درس 04 — Stone Soup & Boiled Frog
## تغییر کوچک ایجاد کن، ولی تصویر بزرگ را فراموش نکن

این بخش دو مفهوم دارد:

1. **Be a Catalyst for Change**
2. **Remember the Big Picture**

---

# 1. Be a Catalyst for Change

گاهی درخواست یک تغییر بزرگ با مقاومت روبه‌رو می‌شود.

مثلاً پروژه Data Fetching نامنسجم دارد:

```ts
fetch("/api/users");
fetch("/api/orders");
fetch("/api/products");
```

اگر بگویی:

> کل پروژه را ببریم روی React Query.

ممکن است تیم آن را یک Migration بزرگ و پرریسک ببیند.

راه پراگماتیک‌تر:

یک Feature مستقل را با Pattern بهتر پیاده کن.

```tsx
function UsersPage() {
  const {
    data,
    isLoading,
    error,
  } = useQuery({
    queryKey: ["users"],
    queryFn: getUsers,
  });

  if (isLoading) return <Loading />;
  if (error) return <ErrorState />;

  return <UsersList users={data} />;
}
```

بعد نتیجه را نشان بده:

```text
قبل:
- Loading دستی
- Error دستی
- Duplicate Request
- Boilerplate زیاد

بعد:
- Cache
- Retry
- مدیریت Loading
- کد کمتر
```

این یعنی:

> Proof of Value قبل از Change بزرگ

---

## Catalyst ≠ Chaos

این درست نیست:

> بدون هماهنگی کل Redux را به Zustand مهاجرت کردم.

این منطقی‌تر است:

> برای Feature مستقل جدید Zustand را امتحان کردم. اگر تیم موافق باشد می‌توانیم Pattern را برای موارد مشابه بررسی کنیم.

---

# 2. Boiled Frog

گاهی خراب شدن پروژه ناگهانی نیست.

مثلاً:

```text
Dashboard.tsx
250 lines
↓
320
↓
420
↓
560
↓
730
↓
900
↓
1374
```

هیچ روز مشخصی وجود ندارد که بگویی:

> امروز Architecture خراب شد.

مشکل به‌تدریج جمع شده است.

---

## فرق Broken Window و Boiled Frog

### Broken Window

خرابی واضح وجود دارد و همه می‌بینند، ولی کسی اصلاحش نمی‌کند.

```text
خرابی واضح
 ↓
بی‌توجهی
 ↓
خرابی‌های بیشتر
```

### Boiled Frog

تغییرها آن‌قدر کوچک‌اند که جهت کلی پروژه دیده نمی‌شود.

```text
تغییر کوچک
 ↓
تغییر کوچک
 ↓
تغییر کوچک
 ↓
Complexity زیاد
```

---

## مثال React

ابتدا:

```tsx
const [product, setProduct] = useState<Product>();
```

بعد:

```tsx
const [loading, setLoading] = useState(false);
const [error, setError] = useState<string>();
const [reviews, setReviews] = useState<Review[]>([]);
const [recommendations, setRecommendations] = useState<Product[]>([]);
const [selectedVariant, setSelectedVariant] = useState<Variant>();
const [discount, setDiscount] = useState<Discount>();
```

هیچ‌کدام جداگانه الزاماً اشتباه نیست.

اما یک جایی باید بپرسی:

> آیا این Component هنوز فقط یک Responsibility دارد؟

---

## Senior Mindset

Junior فقط Ticket را می‌بیند:

```text
Add discount badge
```

Senior تصویر بزرگ‌تر را هم می‌بیند:

```text
Add discount badge
        ↓
ProductPage already has 12 responsibilities
        ↓
Adding this increases complexity
        ↓
Maybe extract pricing logic
```

---

## نشانه‌های بالا رفتن دمای آب

هر چند وقت یک بار بپرس:

- آیا Architecture هنوز قابل فهم است؟
- آیا Complexity رو به افزایش است؟
- آیا Featureها بیش از حد به هم وابسته‌اند؟
- آیا Componentها بیش از حد بزرگ شده‌اند؟
- آیا سرعت توسعه نسبت به قبل پایین آمده؟
- آیا Bugها بیشتر شده‌اند؟
- آیا برای یک تغییر کوچک باید ده فایل را تغییر بدهم؟

---

## تمرین

اگر پوشه `components` به ۱۸۰ فایل رسیده و Feature Boundary مشخصی ندارد:

```text
src/
  components/
    Button.tsx
    Modal.tsx
    UserTable.tsx
    PaymentTable.tsx
    PaymentForm.tsx
    ...
```

ممکن است هم Broken Window باشد و هم Boiled Frog.

برای Feature جدید بهتر است ساختار واضح‌تری بسازی:

```text
features/
  payments/
    components/
    hooks/
    services/
    types/
```
