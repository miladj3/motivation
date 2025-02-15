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