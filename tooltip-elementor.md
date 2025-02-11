# افزودن تولتیپ (Tooltip) به ویجت‌های المنتور بدون افزونه

این آموزش به شما نشان می‌دهد چگونه بدون استفاده از افزونه، به ویجت‌های المنتور تولتیپ اضافه کنید. این روش با استفاده از CSS سفارشی انجام می‌شود و به شما امکان می‌دهد تولتیپ‌های زیبا و کاربردی برای عناصر مختلف سایت خود ایجاد کنید.

## 1. افزودن کد CSS به بخش CSS سفارشی سایت

برای شروع، کد CSS زیر را به بخش "CSS سفارشی" در تنظیمات قالب یا المنتور خود اضافه کنید. این کد استایل اصلی تولتیپ را تعریف می‌کند.

```css
.custom-tooltip {
    position: relative;
    display: inline-block; /* برای قرارگیری صحیح تولتیپ */
    cursor: pointer;      /* تغییر نشانگر موس برای راهنمایی کاربر */
}
```css
```css

/* استایل اصلی تولتیپ */
.custom-tooltip::after {
    content: attr(data-tooltip); /* محتوای تولتیپ از attribute 'data-tooltip' گرفته می‌شود */
    position: absolute;
    background: rgba(0, 0, 0, 0.85); /* رنگ پس‌زمینه تولتیپ */
    color: #fff;                     /* رنگ متن تولتیپ */
    padding: 8px 12px;               /* فاصله‌ی داخلی تولتیپ */
    border-radius: 5px;              /* گردی گوشه‌های تولتیپ */
    font-size: 14px;                 /* اندازه‌ی فونت تولتیپ */
    white-space: nowrap;             /* جلوگیری از شکستن متن تولتیپ به خطوط جدید */
    visibility: hidden;              /* مخفی بودن تولتیپ در حالت عادی */
    opacity: 0;                     /* شفافیت صفر برای انیمیشن نمایش */
    transition: opacity 0.3s, visibility 0.3s; /* انیمیشن برای نمایش و پنهان شدن تولتیپ */
    z-index: 999;                    /* اطمینان از نمایش تولتیپ روی سایر عناصر */
}

/* نمایش تولتیپ هنگام هاور (Hover) */
.custom-tooltip:hover::after {
    visibility: visible; /* نمایش تولتیپ */
    opacity: 1;        /* نمایش کامل تولتیپ با شفافیت 1 */
}

/* موقعیت پیش‌فرض تولتیپ: بالا */
.custom-tooltip[data-tooltip-position="top"]::after,
.custom-tooltip:not([data-tooltip-position])::after { /* اگر موقعیت مشخص نشده، بالا در نظر گرفته شود */
    bottom: 120%;      /* موقعیت تولتیپ نسبت به پایین عنصر */
    left: 50%;        /* موقعیت افقی تولتیپ در مرکز عنصر */
    transform: translateX(-50%); /* تنظیم دقیق مرکز تولتیپ */
}

/* موقعیت تولتیپ: پایین */
.custom-tooltip[data-tooltip-position="bottom"]::after {
    top: 120%;         /* موقعیت تولتیپ نسبت به بالای عنصر */
    left: 50%;        /* موقعیت افقی تولتیپ در مرکز عنصر */
    transform: translateX(-50%); /* تنظیم دقیق مرکز تولتیپ */
}

/* موقعیت تولتیپ: چپ */
.custom-tooltip[data-tooltip-position="left"]::after {
    right: 120%;       /* موقعیت تولتیپ نسبت به راست عنصر */
    top: 50%;         /* موقعیت عمودی تولتیپ در مرکز عنصر */
    transform: translateY(-50%); /* تنظیم دقیق مرکز تولتیپ */
}

/* موقعیت تولتیپ: راست */
.custom-tooltip[data-tooltip-position="right"]::after {
    left: 120%;        /* موقعیت تولتیپ نسبت به چپ عنصر */
    top: 50%;         /* موقعیت عمودی تولتیپ در مرکز عنصر */
    transform: translateY(-50%); /* تنظیم دقیق مرکز تولتیپ */
}

/* تنظیمات ریسپانسیو برای موبایل */
@media (max-width: 768px) {
    .custom-tooltip::after {
        top: 120% !important;    /* نمایش تولتیپ در بالا در موبایل */
        left: 50%;              /* موقعیت افقی تولتیپ در مرکز عنصر */
        transform: translateX(-50%) !important; /* تنظیم دقیق مرکز تولتیپ */
    }
}
