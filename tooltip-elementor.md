#add tooltip for elementor whitout plugin | افزودن تولتیپ به ویجت های المنتور بدون افزونه 

##1- CSS in custom css | افزودن کد سی اس اس به کل سایت 
code :"
.custom-tooltip {
    position: relative;
    display: inline-block;
    cursor: pointer; /* برای نمایش بهتر برای کاربر */
}

/* تولتیپ */
.custom-tooltip::after {
    content: attr(data-tooltip); /* دریافت متن از data-tooltip */
    position: absolute;
    background: rgba(0, 0, 0, 0.85);
    color: #fff;
    padding: 8px 12px;
    border-radius: 5px;
    font-size: 14px;
    white-space: nowrap;
    visibility: hidden;
    opacity: 0;
    transition: opacity 0.3s, visibility 0.3s;
    z-index: 999;
}

/* نمایش تولتیپ روی هاور */
.custom-tooltip:hover::after {
    visibility: visible;
    opacity: 1;
}

/* تنظیمات موقعیت تولتیپ */
.custom-tooltip[data-tooltip-position="top"]::after,
.custom-tooltip:not([data-tooltip-position])::after {
    bottom: 120%;
    left: 50%;
    transform: translateX(-50%);
}

.custom-tooltip[data-tooltip-position="bottom"]::after {
    top: 120%;
    left: 50%;
    transform: translateX(-50%);
}

.custom-tooltip[data-tooltip-position="left"]::after {
    right: 120%;
    top: 50%;
    transform: translateY(-50%);
}

.custom-tooltip[data-tooltip-position="right"]::after {
    left: 120%;
    top: 50%;
    transform: translateY(-50%);
}

/* ریسپانسیو برای موبایل */
@media (max-width: 768px) {
    .custom-tooltip::after {
        top: 120% !important;
        left: 50%;
        transform: translateX(-50%) !important;
    }
}
"


## possion tooltip |  محل نمایش تولتیپ 


data-tooltip-position|bottom
✅ تولتیپ در چپ
data-tooltip|متن تولتیپ
✅ تولتیپ در پایین
data-tooltip|متن تولتیپ

data-tooltip|متن تولتیپ
data-tooltip-position|left
✅ تولتیپ در راست
data-tooltip|متن تولتیپ
data-tooltip-position|right



## add css class to element |  افزودن کلاس  سی اس اس به ویجت المنتور مورد نظر 
