# درس 03 — Software Entropy & Broken Windows
## آنتروپی نرم‌افزار و پنجره‌های شکسته

## Software Entropy چیست؟

در نرم‌افزار هم مثل یک سیستم واقعی، اگر مراقبت نشود بی‌نظمی افزایش پیدا می‌کند.

نشانه‌ها:

- Componentهای خیلی بزرگ
- `any`های زیاد
- Naming نامنسجم
- Duplicate Logic
- Coupling زیاد
- Error Handling ناقص
- TODOهای رهاشده

---

## مثال ساده

امروز:

```ts
if (user.role === "admin") {
  // ...
}
```

فردا:

```ts
if (user.type === "ADMIN") {
  // ...
}
```

بعد:

```ts
if (user.permissions.includes("admin")) {
  // ...
}
```

سه Implementation برای یک Concept.

Developer بعدی می‌گوید:

> پروژه خودش همین‌طوری است.

و چهارمین روش را اضافه می‌کند.

این یعنی Entropy در حال رشد است.

---

# Broken Window

یک خرابی کوچک وقتی مدت زیادی باقی بماند، به تیم پیام می‌دهد:

> «اینجا کسی به کیفیت اهمیت نمی‌دهد.»

مثلاً:

```ts
const data: any = response.data;
```

اگر پروژه پر از `any` باشد، Developer جدید هم راحت‌تر `any` اضافه می‌کند.

یا:

```ts
try {
  // ...
} catch (e) {}
```

یا:

```tsx
function Dashboard() {
  // 1200 lines...
}
```

---

## واکنش درست چیست؟

قرار نیست همیشه کل سیستم را Refactor کنی.

اما نباید خرابی جدید اضافه کنی.

مثلاً:

```ts
const calculateTotal = (items: any[]) => {
  // old logic
};
```

اگر Feature جدید همین قسمت را لمس می‌کند، حداقل Boundary مرتبط را تمیز کن:

```ts
type CartItem = {
  id: number;
  price: number;
  quantity: number;
};

function calculateTotal(items: CartItem[]): number {
  return items.reduce(
    (total, item) => total + item.price * item.quantity,
    0
  );
}
```

---

## قانون مفید

> Leave the code a little better than you found it.

اما مراقب باش تبدیل نشود به:

> هر فایل بدی دیدم باید همین الان Refactor کنم.

Scope مهم است.

---

## تصمیم‌گیری

```text
کد قدیمی مشکل دارد
        ↓
آیا مستقیم در Scope من است؟
        ↓
      بله
        ↓
می‌توانم با ریسک کم اصلاحش کنم؟
   ↙              ↘
 بله               نه
  ↓                 ↓
اصلاح محدود       Boundary امن
                    +
             ثبت Refactor بزرگ‌تر
```

---

## Cohesion و Coupling

### High Cohesion

چیزهایی که مربوط به یک Feature هستند کنار هم باشند:

```text
payments/
  PaymentForm.tsx
  PaymentTable.tsx
  usePayment.ts
  payment.service.ts
```

### Low Coupling

Feature پرداخت برای کار کردن مجبور نباشد جزئیات داخلی ده Feature دیگر را بشناسد.

هدف عمومی:

```text
High Cohesion + Low Coupling
```

---

## تمرین

یک Function مشترک در ۳۵ نقطه استفاده شده:

```ts
export async function getUser(id: number) {
  const res = await fetch(`/api/users/${id}`);
  const data: any = await res.json();

  return data;
}
```

تو فقط در یک Feature به آن نیاز داری.

سه انتخاب:

- A: کل Function و ۳۵ مصرف‌کننده را Refactor کن.
- B: هیچ کاری نکن.
- C: برای Feature خودت Boundary امن بساز و Refactor بزرگ را جدا ثبت کن.

در اغلب شرایط C کم‌ریسک‌تر و پراگماتیک‌تر است.
