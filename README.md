# راهنمای استفاده از قالب مستندات پروژه‌های دانشگاهی 

---
<p align="center">
  <img src="https://github.com/user-attachments/assets/8b21e9bb-56e5-485d-b862-c69ef0218229" alt="screenshot 1" width="45%"/>
  <img src="https://github.com/user-attachments/assets/aa28736a-0446-42ab-afbb-f6ea1dffa168" alt="screenshot 2" width="45%" style="margin-right:10px;"/>
</p>


## پیش‌نیازها

برای استفاده از این قالب، ابتدا باید ابزارهای زیر را روی سیستم خود نصب کنید:

### برای کاربران ویندوز:

* نصب [**MiKTeX**](https://miktex.org/download)

  * پیشنهاد می‌شود نسخه کامل نصب شود.
  * پس از نصب، گزینه "Install missing packages on-the-fly" را فعال کنید.

### برای کاربران لینوکس:

* نصب TeX Live (نسخه کامل):

  ```bash
  sudo apt install texlive-full
  ```

---

## بسته‌های مورد نیاز

این قالب به بسته‌های زیر وابسته است که در `MiKTeX` یا `TeX Live Full` معمولاً از قبل نصب شده‌اند:

* `xepersian` (برای پشتیبانی از زبان فارسی)
* `graphicx` (برای وارد کردن تصاویر)
* `fancyhdr` (برای مدیریت هدر و فوتر)
* `float`, `caption`, `longtable`, `enumitem`, `xcolor`, `hyperref`, `amsmath`
* `fontspec` (به صورت ضمنی با `xepersian` نصب می‌شود)

> اگر از MiKTeX استفاده می‌کنید، ممکن است بسته‌ها در اولین اجرای `xelatex` به‌صورت خودکار نصب شوند.

---

## ساختار فایل‌ها

```
project/
├── doc.tex              % فایل اصلی مستند شما
├── src/
│   ├── template.tex     % قالب و تنظیمات کلی سند
│   ├── cover.tex        % جلد (صفحه اول)
│   ├── fonts/           % فونت‌های فارسی (مثلاً XB Niloofar.ttf)
│   └── images/          % محل ذخیره تصاویر
```

---

## وارد کردن اطلاعات پروژه

برای وارد کردن اطلاعات خود در قالب، کافی‌ست در بالای فایل `doc.tex` مقادیر زیر را تنظیم کنید:

```latex
\newcommand{\coursename}{نام درس}
\newcommand{\projecttitle}{عنوان پروژه}
\newcommand{\teachername}{نام استاد}
\newcommand{\groupmembers}{نام اعضای گروه}
\newcommand{\termname}{مثلاً: بهار ۱۴۰۴}
```

این اطلاعات به‌صورت خودکار در جلد (فایل `cover.tex`) و همچنین در هدر صفحات قرار خواهند گرفت. نیازی به ویرایش دستی `template.tex` یا `cover.tex` نیست.

---

## اضافه کردن محتوای علمی

در فایل `doc.tex`، پس از خطوط زیر:

```latex
\tableofcontents
\newpage

% -----------------------------------------------
% Type here...
```

محتوای خود را به کمک دستورات `\section`, `\subsection` و... وارد کنید.

مثال:

```latex
\section{مقدمه}
در این پروژه بازی چهار مهره در یک ردیف پیاده‌سازی شده است.
```

---

## نوشتن متن فارسی همراه با انگلیسی

برای جلوگیری از به‌هم‌ریختگی متن هنگام ترکیب فارسی و انگلیسی:

### استفاده از `\lr{}` برای کلمات انگلیسی:

```latex
برای ورود به \lr{Settings} به بخش تنظیمات بروید.
```

---

## درج تصویر

برای درج تصویر، از دستور اختصاصی تعریف‌شده در قالب استفاده کنید:

```latex
\settingimage{src/images/sample.png}
```

این دستور تصویر را به‌صورت وسط‌چین و با عرض مناسب در صفحه قرار می‌دهد.

---

## نوشتن لیست‌ها

```latex
\begin{itemize}
  \item مورد اول
  \item مورد دوم
\end{itemize}
```

---

## فهرست مطالب

فهرست مطالب به‌صورت خودکار با توجه به ساختار سند ایجاد می‌شود.

### دستورات مفید:

```latex
\section{...}         % بخش اصلی
\subsection{...}      % زیر‌بخش
\subsubsection{...}   % زیر‌زیر‌بخش
```

> نیازی به اضافه کردن `\tableofcontents` نیست — این دستور در قالب گنجانده شده است. فقط کافی‌ست سند را **دو بار کامپایل** کنید تا شماره صفحات به‌درستی به‌روزرسانی شوند.

---

## نحوه کامپایل گرفتن

### در محیط‌هایی مانند **TeXstudio** یا **Overleaf**:

* اطمینان حاصل کنید که **XeLaTeX** را به عنوان کامپایلر انتخاب کرده‌اید.

### یا در خط فرمان (ترمینال):

```bash
xelatex doc.tex
```

> اگر با خطای فونت مواجه شدید، بررسی کنید که فایل فونت `XB Niloofar.ttf` در مسیر `src/fonts/` قرار داشته باشد.

---

## خروجی نهایی

خروجی قالب، یک فایل PDF با نام `doc.pdf` خواهد بود که در مسیر اصلی قرار می‌گیرد.

این فایل آماده ارائه، ارسال یا چاپ است.


## آموزش راه اندازی لاتک در ویندوز
https://scholarly.so/blog/a-step-by-step-guide-how-to-install-latex-on-windows

## یادگیری لاتک
https://en.wikibooks.org/wiki/LaTeX

## نصب ویرایشگر TexStudio
https://www.texstudio.org
