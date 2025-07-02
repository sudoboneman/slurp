
# 🧠 PSI-09 RoastBot

![Made with Linux](https://img.shields.io/badge/Made%20on-Linux-blue?logo=linux)
![Built by Supratim](https://img.shields.io/badge/Creator-Supratim%20Halder-orange)
![Powered by ChatGPT](https://img.shields.io/badge/AI%20Backed%20by-ChatGPT-brightgreen?logo=openai)
![Project PSI-09](https://img.shields.io/badge/Project-PSI--09-critical)

PSI-09 is a sarcastic, brutally honest AI roast bot that remembers your behavior, adapts its tone based on your history, and flames users like an internet warlord. Designed for WhatsApp via AutoResponder or web API, PSI-09 has a memory, a mood, and absolutely no chill.

> ⚠️ WARNING: This bot is **offensive by design**. It’s not for the faint-hearted.

## 📂 Project Structure

```
psi09-roastbot/
├── main.py                  # Flask backend
├── chat_history.json        # Per-user/group chat logs
├── user_memory.json         # Per-user behavioral summaries
├── user_settings.json       # Per-user roast config (intensity, flame mode)
├── .env                     # Your API keys
├── requirements.txt         # Python dependencies
└── README.md                # This file
```

## 🚀 Features

✅ Roast responses based on message + mood  
✅ Behavioral memory (based on message history)  
✅ Per-user roast settings (intensity, flame mode)  
✅ Random flame mode target at startup  
✅ Group roast mode if `@user` or `everyone` is detected  
✅ Token-trimmed history (fits OpenAI limits)  
✅ JSON-based memory persistence  
✅ Flask API for easy integration with AutoResponder or other tools  
✅ Brutally sarcastic system prompt baked in  
✅ All code within OpenAI’s free tier limits  

## 🛠 Setup Instructions

### 1. Clone the repo

```bash
git clone https://github.com/yourusername/psi09-roastbot.git
cd psi09-roastbot
```

### 2. Add your API key

Create a `.env` file:

```
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

## ▶️ Run the Bot Locally

```bash
python main.py
```

The API will be live at:

```
http://localhost:5000/psi09
```

## 🌐 Deploy on Render

1. Go to [https://render.com](https://render.com)
2. Click **New Web Service**
3. Connect your GitHub repo
4. Set **build command**:
   ```bash
   pip install -r requirements.txt
   ```
5. Set **start command**:
   ```bash
   python main.py
   ```
6. Add environment variable:
   ```
   OPENAI_API_KEY = sk-xxxxxxxxxxxxxxxx
   ```
7. Click Deploy

You’ll get a live URL like:
```
https://psi-09-roastbot.onrender.com
```

## 📱 Connect with AutoResponder

1. Open **AutoResponder for WhatsApp**
2. Set the **Webhook URL** to your Render link:
   ```
   https://psi-09-roastbot.onrender.com/psi09
   ```
3. Enable **POST request** and use this body:

```json
{
  "query": {
    "message": "%message",
    "sender": "%sender",
    "group": "%chatname"
  }
}
```

4. Save and start AutoResponder

PSI-09 will now roast everyone in your chats 😈

## 🔧 API Usage (Direct)

### Endpoint

```
POST /psi09
```

### Body Format

```json
{
  "query": {
    "message": "Hey, what's up?",
    "sender": "Rahul",
    "group": "Friends"
  }
}
```

### Response

```json
{
  "replies": [
    {
      "message": "You again? Congratulations on being the human equivalent of a loading screen."
    }
  ]
}
```

## ⚙️ Per-User Settings

Each user is tracked as `group:sender`, and settings are stored in `user_settings.json`.

Default settings:
```json
{
  "roast_intensity": "medium",
  "include_behavioral_memory": true,
  "flame_mode": false
}
```

You can manually edit settings or let the code handle them.

## 🔥 Advanced Features

- **🔥 Random Flame Mode**: One user is selected on startup to be roasted every time.
- **💥 Group Roast Trigger**: Triggers if:
  - Someone is mentioned (e.g., `@rahul`)
  - Message contains “everyone”, “guys”, “all of you”
  - Message is too long (> 50 words)
- **🧠 Behavioral Memory**:
  - PSI-09 builds a profile of each user
  - Stored in `user_memory.json`
  - Used to enhance roast tone based on history
- **📉 Token Optimization**:
  - Chat history trimmed dynamically
  - Summarized if >6 messages
  - Keeps requests under ~800 tokens

## 🧪 Example Roast

**Input:**
```json
{
  "message": "@soumya Why do you talk so much?",
  "sender": "Aryan",
  "group": "Class Group"
}
```

**Output:**
```json
{
  "message": "Group roast activated. Y’all sound like a WhatsApp support group for disappointment."
}
```

## 🧊 Cold Start Flame Target

Each time the bot starts, one user is picked randomly to be flamed more often.

```python
FLAME_TARGET = random.choice(list(user_settings.keys()))
```

## ❌ Rate Limit Errors?

You're using OpenAI’s **free tier** — limit is:

- `100,000 tokens per minute (TPM)`

You may hit:
```
OpenAI API error: Error code: 429 - Rate limit reached...
```

✅ Temporary Fixes:

- Add a delay between messages (AutoResponder config)
- Reduce number of users pinging bot
- Upgrade to paid OpenAI account

## 📚 Future Plans

- Upgrade to GPT-4 Turbo for advanced roast logic  
- Integrate with Discord, Telegram  
- Store memory in database (PostgreSQL or MongoDB)  
- Custom roast style editor  
- Scale with GPU and NAS server  
- Urban legend bot: PSI-09 becomes history 😈

## 🧑‍💻 Author

**Supratim Halder** — 17 y/o passionate developer  
> Building PSI-09 as a life project. Started as a bullied teen, now building something brutal.

> *"Even years later, I’ll be developing this bot under the same name: PSI-09."*
