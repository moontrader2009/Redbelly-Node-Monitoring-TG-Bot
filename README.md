# 🛡️ Redbelly Node Telegram Monitor Bot

A Bash script to monitor the health and performance of a Redbelly blockchain node. It sends periodic status updates and critical alerts to a configured Telegram chat for seamless node monitoring.

---

## 📌 Features

- ✅ Check node synchronization status against the latest blockchain height  
- 📟 Monitor node process status (e.g., `rbbc` process)  
- 🧠 Report system metrics:  
  - CPU usage  
  - Memory usage  
  - Disk usage  
  - Load average  
- 🔐 Monitor SSL certificate expiration for a specified domain  
- 👑 Evaluate local governor status via node metrics  
- 💸 Fetch and report RBNT balances for voting and signing addresses  
- 📊 Send detailed status reports to Telegram  
- 🚨 Send real-time alerts for:  
  - Block lag exceeding threshold  
  - Low RBNT voting balance  
  - Node process not running  
  - Node not fully synced  

---

## 🚀 Setup & Usage

### 1. Create a Telegram Bot

- Open Telegram and search for `@BotFather`
- Send `/newbot` and follow instructions to create your bot  
- Copy the **Bot Token** provided by BotFather

### 2. Get Your Telegram Chat ID

- Start a chat with your new bot  
- Send any message to your bot  
- Use the following URL in your browser (replace `YOUR_BOT_TOKEN`): https://api.telegram.org/botYOUR_BOT_TOKEN/getUpdates
- Look for `"chat":{"id":YOUR_CHAT_ID}` in the JSON response  
- Save the `YOUR_CHAT_ID`

### 📝 Step-by-Step: Create `redbelly_monitor.sh` and Configure

Follow these steps to set up the monitoring script on your node:

### 1. Open your terminal
### 2. Create or open the script file using nano

```bash
nano redbelly_monitor.sh
```
### 3. Paste the script content  
- Copy the script from this GitHub link:
- Paste it into the terminal `(Ctrl + Shift + V)`
