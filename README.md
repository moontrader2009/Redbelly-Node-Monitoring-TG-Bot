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
## ⚙️ Configuring Redbelly Node HTTP API Access
To enable the Redbelly node HTTP RPC interface and allow external access, the following flags must be added to the node startup command:
```bash
--http --http.addr=0.0.0.0 --http.corsdomain=* --http.vhosts=* --http.port=8545 --http.api eth,txpool,net,web3,rbn
```
### Steps to add the flags:
1. Edit the systemd service file:
```bash
sudo nano /etc/systemd/system/redbelly.service
```
2. Locate the `ExecStart` line and append the HTTP flags.
3. Save and exit the file
4. Reload systemd and restart the node service:
```bash
sudo systemctl daemon-reload
sudo systemctl restart redbelly.service
sudo systemctl status redbelly.service
```
---
## 🚀 Setup & Usage

### 1. Create a Telegram Bot

- Open Telegram and search for `@BotFather`
- Send `/newbot` and follow instructions to create your bot  
- Copy the **Bot Token** provided by BotFather

### 2. Get Your Telegram Chat ID

- Start a chat with your new bot  
- Send any message to your bot  
- Use the following URL in your browser (replace `YOUR_BOT_TOKEN`): `https://api.telegram.org/botYOUR_BOT_TOKEN/getUpdates`
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
- Copy the script from this [GitHub link](https://github.com/moontrader2009/Redbelly-Node-Monitoring-TG-Bot/blob/main/Redbelly%20Node%20Monitoring%20Bot.txt)  
- Paste it into the terminal `(Ctrl + Shift + V)`
  
### 4. Configure the script
- Scroll to the `# === CONFIGURATION ===` section at the top of the script and update the following values:
```bash
TELEGRAM_BOT_TOKEN="your_telegram_bot_token"
CHAT_ID="your_telegram_chat_id"
THRESHOLD=1000
BALANCE_THRESHOLD=100
VOTING_ADDRESS="your_voting_address"
SIGNING_ADDRESS="your_signing_address"
NODE_ENDPOINT="https://localhost:8545"
CHAIN_ENDPOINT="https://governors.mainnet.redbelly.network"
DOMAIN="yourdomain.com"
```
### 5. Save and exit nano
- Press `Ctrl + O` to save
- Press `Enter` to confirm
- Press `Ctrl + X` to exit
- 
### 6. Make the script executable
```bash
chmod +x redbelly_monitor.sh
```
### 7. Run the script
```bash
./redbelly_monitor.sh
```
### ⏱️ Optional: Automate with Cron
To run the script at regular intervals:
```bash
crontab -e
```
Add this line to run every 5 minutes (adjust as needed):
```bash
*/5 * * * * /path/to/redbelly_monitor.sh
```

