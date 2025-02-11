# افزودن تولتیپ (Tooltip) به ویجت‌های المنتور بدون افزونه

این آموزش به شما نشان می‌دهد چگونه بدون استفاده از افزونه، به ویجت‌های المنتور تولتیپ اضافه کنید. این روش با استفاده از CSS سفارشی انجام می‌شود و به شما امکان می‌دهد تولتیپ‌های زیبا و کاربردی برای عناصر مختلف سایت خود ایجاد کنید.

## 1. افزودن کد CSS به بخش CSS سفارشی سایت

برای شروع، کد CSS زیر را به بخش "CSS سفارشی" در تنظیمات قالب یا المنتور خود اضافه کنید. این کد استایل اصلی تولتیپ را تعریف می‌کند.

```css

/* استایل اصلی تولتیپ */
.ht::after {
    background: rgba(255, 254, 254, 0.8);
box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
backdrop-filter: blur(9.1px);
-webkit-backdrop-filter: blur(9.1px);
border: 1px solid rgba(255, 254, 254, 1);
    content: attr(data-tooltip); /* دریافت متن از اتریبیوت */
    position: absolute;
    color: #1A374D;
    padding: 8px 12px;
    border-radius: 5px;
    font-size: 12px;
    font-family: 'matn';
    width: 100%;
    visibility: hidden;
    opacity: 0;
    transition: opacity 0.3s, visibility 0.3s;
    z-index: 999;
}

/* نمایش در بالا */
.ht[data-tooltip-position="top"]::after{
    bottom: 120%;
    left: 50%;
    transform: translateX(-50%);
}

/*  حالت پیش‌فرض: نمایش در پایین */
.ht[data-tooltip-position="bottom"]::after, .ht:not([data-tooltip-position])::after {
    top: 120%;
    left: 50%;
    transform: translateX(-50%);
}

/* نمایش در چپ */
.ht[data-tooltip-position="left"]::after {
    right: 120%;
    top: 50%;
    transform: translateY(-50%);
}

/* نمایش در راست */
.ht[data-tooltip-position="right"]::after {
    left: 120%;
    top: 50%;
    transform: translateY(-50%);
}

/* نمایش تولتیپ هنگام هاور */
.ht:hover::after {
    visibility: visible;
    opacity: 1;
}
```
```css
/* برای موبایل: نمایش تولتیپ فقط در پایین */
@media (max-width: 768px) {
    .ht::after {
        top: 120% !important;
        left: 50%;
        transform: translateX(-50%) !important;
    }
}
```

## 2. افزودن کلاس css به المان مورد نظر 
باید کلاس .ht رو به المان مورد نظر خودمون بدیم 

```css
.ht
```

## 3. افزودن اتریبیوت مورد نظر به المان مورد نظر 

### اتریبیوت اول :  data-tooltip
```html
data-tooltip|متن تولتیپ
```

###  اتریبیوت دوم : data-tooltip-position 
محل قرار گیری تولتیپ مورد نظر


```html
data-tooltip-position|bottom
```
```html
data-tooltip-position|left
```
```html
data-tooltip-position|right
```
```html
data-tooltip-position|top
```
