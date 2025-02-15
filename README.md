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

## 2. How to Start the Bot and Get Chat ID

1. **Search for your bot** in Telegram using the username you created (e.g., `DollarRateBot_bot`).
2. Start a chat with your bot by clicking on the **Start** button.
3. To get the **Chat ID**, you can use the following method:
   - Send a message to your bot (e.g., "Hello").
   - Use the following URL in your browser to get the chat ID:
     ```
     https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates
     ```
     Replace `<YOUR_BOT_TOKEN>` with the token you received from BotFather.
   - Look for the `chat` object in the JSON response. The `id` field is your **Chat ID**.
     Example:
     ```json
     {
       "update_id": 123456789,
       "message": {
         "chat": {
           "id": 987654321,
           "first_name": "John",
           "type": "private"
         },
         "text": "Hello"
       }
     }
     ```
   - In this example, the **Chat ID** is `987654321`.

4. **Save the Chat ID** securely, as you will need it for the GitHub Action.

## 3. How to Fork and Create 4 Action Secrets in GitHub Action

### Fork the Repository

1. Go to the GitHub repository containing the `Dollar.yml` file.
2. Click the **Fork** button in the top-right corner to create a copy of the repository in your GitHub account.

### Create Secrets in GitHub

1. Go to your forked repository on GitHub.
2. Click on the **Settings** tab.
3. In the left sidebar, click on **Secrets and variables** > **Actions**.
4. Click on the **New repository secret** button to create the following secrets:

   - **TELEGRAM_BOT_TOKEN**: The token you received from BotFather.
   - **TELEGRAM_CHAT_ID**: The Chat ID you obtained from the `getUpdates` API call.
   - **NUMBER**: A secret number that will be used in the calculation (e.g., `1000000`).
   - **MESSAGE**: A custom message that will be sent along with the result (e.g., "Dollars").

5. After creating all four secrets, your GitHub Action will be able to use them to fetch the dollar rate, perform calculations, and send the result to your Telegram bot.

### Verify the Workflow

1. Go to the **Actions** tab in your forked repository.
2. Ensure that the workflow is enabled and running on the schedule defined in the `Dollar.yml` file (every day at 10 AM Iran Time).
3. You should receive a message in your Telegram bot with the calculated result and the custom message.

---

By following these steps, you will have a fully functional GitHub Action that fetches the dollar rate, performs a calculation, and sends the result to your Telegram bot.