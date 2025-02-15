<div dir="rtl">

# راهنمای راه‌اندازی ربات تلگرام و GitHub Action

این راهنما شما را گام‌به‌گام برای راه‌اندازی یک ربات تلگرام، دریافت اعتبارنامه‌های لازم و پیکربندی GitHub Action برای دریافت نرخ دلار و ارسال آن به تلگرام راهنمایی می‌کند.

## ۱. چگونه یک ربات در تلگرام ایجاد کنیم و توکن ربات را دریافت کنیم

۱. **تلگرام** را باز کنید و **BotFather** (ربات رسمی تلگرام برای ایجاد و مدیریت ربات‌ها) را جستجو کنید.  
۲. با کلیک روی دکمه **Start**، چت با BotFather را شروع کنید.  
۳. از دستور `/newbot` برای ایجاد یک ربات جدید استفاده کنید.  
۴. دستورالعمل‌ها را دنبال کنید:  
   - یک نام برای ربات خود انتخاب کنید (مثلاً `DollarRateBot`).  
   - یک نام کاربری برای ربات خود انتخاب کنید (باید با `bot` پایان یابد، مثلاً `DollarRateBot_bot`).  
۵. پس از ایجاد ربات، BotFather یک **توکن** به شما می‌دهد. این توکن کلید API ربات شماست و برای تعامل با API تلگرام استفاده می‌شود.  
   - مثال توکن: `123456789:ABCdefGhIJKlmNoPQRstuVWXyz`  

۶. **توکن را ذخیره کنید**، زیرا برای GitHub Action به آن نیاز خواهید داشت.  

۷. **ربات خود را شروع کنید** با کلیک روی نام کاربری که در پیام BotFather ارائه شده است. این کار یک چت با ربات جدید شما باز می‌کند.  

## ۲. چگونه شناسه کاربری (Chat ID) را با استفاده از @userinfobot دریافت کنیم

۱. **تلگرام** را باز کنید و **@userinfobot** را جستجو کنید.  
۲. با کلیک روی دکمه **Start**، چت با ربات را شروع کنید.  
۳. ربات به طور خودکار با **شناسه کاربری** شما پاسخ می‌دهد.  
   - مثال پاسخ:  
     ```
     👤 شناسه شما: 123456789
     ```  
۴. **شناسه کاربری را ذخیره کنید**، زیرا این شماره معادل **Chat ID** شماست و در GitHub Action استفاده خواهد شد.  

## ۳. چگونه ریپازیتوری را فورک کنیم و ۴ راز اکشن در GitHub Action ایجاد کنیم

### فورک ریپازیتوری

۱. روی دکمه **Fork** در گوشه بالا سمت راست کلیک کنید تا یک کپی از ریپازیتوری در حساب GitHub شما ایجاد شود.  

### ایجاد رازها در GitHub

۱. به ریپازیتوری فورک‌شده خود در GitHub بروید.  
۲. روی تب **Settings** کلیک کنید.  
۳. در نوار کناری سمت چپ، روی **Secrets and variables** > **Actions** کلیک کنید.  
۴. روی دکمه **New repository secret** کلیک کنید تا رازهای زیر را ایجاد کنید:  

   - **TELEGRAM_BOT_TOKEN**: توکنی که از BotFather دریافت کرده‌اید.  
   - **TELEGRAM_CHAT_ID**: شناسه کاربری که از @userinfobot دریافت کرده‌اید.  
   - **NUMBER**: یک عدد مخفی که در محاسبه استفاده می‌شود (مثلاً `1000000`).  
   - **MESSAGE**: یک پیام سفارشی که همراه با نتیجه ارسال می‌شود (مثلاً "دلار").  

۵. پس از ایجاد همه چهار راز، GitHub Action شما قادر خواهد بود از آن‌ها برای دریافت نرخ دلار، انجام محاسبات و ارسال نتیجه به ربات تلگرام شما استفاده کند.  

### بررسی Workflow

۱. به تب **Actions** در ریپازیتوری فورک‌شده خود بروید.  
۲. مطمئن شوید که workflow فعال است و بر اساس زمان‌بندی تعریف‌شده در فایل `Dollar.yml` (هر روز ساعت ۱۰ صبح به وقت ایران) اجرا می‌شود.  
۳. شما باید یک پیام در ربات تلگرام خود با نتیجه محاسبه‌شده و پیام سفارشی دریافت کنید.  

---

با دنبال کردن این مراحل، شما یک GitHub Action کاملاً کاربردی خواهید داشت که نرخ دلار را دریافت می‌کند، محاسبات را انجام می‌دهد و نتیجه را به ربات تلگرام شما ارسال می‌کند.

</div>

---

# Guide for Setting Up Telegram Bot and GitHub Action

This guide will walk you through the steps required to set up a Telegram bot, obtain the necessary credentials, and configure the GitHub Action to fetch the dollar rate and send it to Telegram.

## 1. How to Create a Bot in Telegram and Get Bot Token

1. **Open Telegram** and search for the **BotFather** (Telegram's official bot for creating and managing bots).
2. Start a chat with BotFather by clicking on the **Start** button.
3. Use the `/newbot` command to create a new bot.
4. Follow the instructions:
   - Choose a name for your bot (e.g., `DollarRateBot`).
   - Choose a username for your bot (must end with `bot`, e.g., `DollarRateBot_bot`).
5. Once the bot is created, BotFather will provide you with a **token**. This token is your bot's API key and will be used to interact with the Telegram API.
   - Example token: `123456789:ABCdefGhIJKlmNoPQRstuVWXyz`

6. **Save the token** securely, as you will need it for the GitHub Action.

7. **Start your bot** by clicking on the username provided in the BotFather's message. This will open a chat with your newly created bot.

## 2. How to Get User ID (Chat ID) Using @userinfobot

1. **Open Telegram** and search for the **@userinfobot**.
2. Start a chat with the bot by clicking on the **Start** button.
3. The bot will automatically reply with your **User ID**.
   - Example response:
     ```
     👤 Your ID: 123456789
     ```
4. **Save the User ID** securely, as this number is equivalent to your **Chat ID** and will be used in the GitHub Action.

## 3. How to Fork and Create 4 Action Secrets in GitHub Action

### Fork the Repository

1. Click the **Fork** button in the top-right corner to create a copy of the repository in your GitHub account.

### Create Secrets in GitHub

1. Go to your forked repository on GitHub.
2. Click on the **Settings** tab.
3. In the left sidebar, click on **Secrets and variables** > **Actions**.
4. Click on the **New repository secret** button to create the following secrets:

   - **TELEGRAM_BOT_TOKEN**: The token you received from BotFather.
   - **TELEGRAM_CHAT_ID**: The User ID you obtained from @userinfobot.
   - **NUMBER**: A secret number that will be used in the calculation (e.g., `1000000`).
   - **MESSAGE**: A custom message that will be sent along with the result (e.g., "Dollars").

5. After creating all four secrets, your GitHub Action will be able to use them to fetch the dollar rate, perform calculations, and send the result to your Telegram bot.

### Verify the Workflow

1. Go to the **Actions** tab in your forked repository.
2. Ensure that the workflow is enabled and running on the schedule defined in the `Dollar.yml` file (every day at 10 AM Iran Time).
3. You should receive a message in your Telegram bot with the calculated result and the custom message.

---

By following these steps, you will have a fully functional GitHub Action that fetches the dollar rate, performs a calculation, and sends the result to your Telegram bot.