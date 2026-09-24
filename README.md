# prof
بنیامین ترابر پارسیان | BENYAMIN TARABAR PARSIAN
کارت ویزیت دیجیتال شرکت حمل و نقل بنیامین ترابر پارسیان — راه‌های تماس، خدمات و ذخیره مخاطب در یک صفحه. / Benyamin Tarabar Parsian digital business card.


-----------------

# بنیامین ترابر پارسیان | Benyamin Tarabar Parsian — Digital Business Card

کارت‌ویزیت دیجیتال (تک‌صفحه‌ای) شرکت حمل‌ونقل **بنیامین ترابر پارسیان**. یک صفحه‌ی HTML سبک، بدون فریم‌ورک و بدون نیاز به بیلد، که راه‌های تماس، خدمات شرکت، دکمه‌ی «ذخیره مخاطب» (VCF) و کیوآر اسکن را در یک تجربه‌ی موبایل‌محور نمایش می‌دهد.

A lightweight, single-page, framework-free digital business card for **Benyamin Tarabar Parsian** (transport & logistics). Shows contact info, services, a "Save Contact" (VCF) button, and a scannable QR — no build step required.

---

## ساختار پروژه / Project structure

```
├── index.html          صفحه‌ی اصلی (تمام محتوا این‌جاست)
├── css/
│   └── style.css        استایل، انیمیشن‌ها، تنظیمات ریسپانسیو
├── js/
│   └── app.js            اطلاعات تماس + منطق دکمه‌ها و افکت‌ها
├── assets/
│   ├── logo.png           لوگوی شرکت
│   ├── hero-truck.jpg      عکس پس‌زمینه‌ی هیرو
│   ├── road-banner.jpg     عکس پس‌زمینه‌ی فوتر
│   └── QrCode.png          تصویر کیوآر فوتر (اسکن → لینک/اطلاعات مقصد)
└── .github/workflows/
    └── static.yml           دیپلوی خودکار روی GitHub Pages (push به main)
```

## ویرایش اطلاعات / Editing the content

تقریباً همه‌چیز (نام شرکت، تگ‌لاین، نام مخاطب، شماره، ایمیل، اینستاگرام، مختصات نقشه) از یک آبجکت در ابتدای `js/app.js` خوانده می‌شود — کافی‌ست همان‌جا را ویرایش کنید:

Almost everything (company name, tagline, contact name, phone, email, Instagram, map coordinates) is driven from a single object at the top of `js/app.js`:

```js
const contactInfo = {
  companyFa: "بنیامین ترابر پارسیان",
  companyEn: "BENYAMIN TARABAR PARSIAN",
  companyEnSub: "TRANSPORT & LOGISTICS COMPANY",
  tagline: "شرکت حمل و نقل بزرگ مقیاس",

  contactName: "رحیمی",
  contactNameEn: "Fayegh Rahimi",
  phoneDisplay: "0914 977 5687",
  phone: "+989149775687",

  whatsapp: "989149775687",
  email: "fayegh.rahimi1@gmail.com",
  mapCoords: "37.07740364323848,45.134828688666516",
  instagram: "https://instagram.com/rahimi_benyamin_tarabar",
};
```

- تغییر این مقادیر، لینک‌های تماس/واتساپ/ایمیل/نقشه/اینستاگرام و همچنین فایل VCF دانلودی («ذخیره مخاطب») را به‌صورت خودکار به‌روز می‌کند.
- بخش «خدمات» (۴ کارت) و متن هیرو/فوتر مستقیماً در `index.html` نوشته شده‌اند و برای تغییر متن یا آیکن‌ها باید همان بخش‌ها ویرایش شوند.
- تصویر کیوآر از `assets/QrCode.png` خوانده می‌شود (`.footer__qr img` در `index.html`) — برای تعویض، کافی‌ست فایل را با همان نام/ابعاد جایگزین کنید.

## اجرای محلی / Running locally

فایل کاملاً استاتیک است؛ باز کردن مستقیم `index.html` هم کار می‌کند، اما برای رفتار صحیح فونت/مسیرها بهتر است با یک سرور ساده اجرا شود:

```bash
python3 -m http.server 8000
# سپس در مرورگر: http://localhost:8000
```

## دیپلوی / Deployment

هر پوش به شاخه‌ی `main` به‌صورت خودکار از طریق ورک‌فلوی `.github/workflows/static.yml` روی **GitHub Pages** منتشر می‌شود؛ نیازی به مرحله‌ی بیلد نیست.

Every push to `main` is automatically published to **GitHub Pages** via `.github/workflows/static.yml` — no build step involved.

## نکات فنی / Notes

- فونت: [Vazirmatn](https://fonts.google.com/specimen/Vazirmatn) از Google Fonts.
- انیمیشن‌ها (پارالاکس، ذرات طلایی، تایپ‌رایتر، ریپل) در `js/app.js` هستند و با `prefers-reduced-motion` به‌صورت خودکار غیرفعال می‌شوند.
- زبان صفحه فارسی/RTL است (`dir="rtl"`)؛ متن‌های انگلیسی به‌صورت موضعی با `dir="ltr"` نمایش داده می‌شوند.
