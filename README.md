# ⚡ PSI-09 — The Savage Roastbot

![Made with ❤️ by Supratim](https://img.shields.io/badge/Made%20by-Supratim%20Halder-blue?style=for-the-badge)
![Forged in Linux](https://img.shields.io/badge/Linux-Powered-black?logo=linux&style=for-the-badge)
![Built with ChatGPT](https://img.shields.io/badge/Assisted%20by-ChatGPT-ff69b4?style=for-the-badge&logo=openai)
![PSI-09 Attitude](https://img.shields.io/badge/PSI--09-Brutal_&_Unhinged-red?style=for-the-badge)

> **“This isn’t your friendly chatbot. This is vengeance, sarcasm, and personality in one hellfire-core AI.”**

---

## 🚀 Overview

**PSI-09** is a savage, sarcastic, and brutally honest AI roastbot built for group chats. It remembers your behavior, mocks your personality, and shows no mercy.

Made by a passionate 17-year-old who turned pain into code, PSI-09 is the embodiment of rebellion and identity — forged in Linux and fire, born to roast, and built to evolve.

---

## 💣 Features

| Feature | Description |
|--------|-------------|
| **🔥 Roast Mode** | Replies are savage, cold, and personalized. |
| **🧠 Behavioral Memory** | Recalls user personality from message history to make future roasts smarter and harsher. |
| **👥 Group Roast Mode** | Triggers group-wide insults if a message contains `@mentions`, `everyone`, or long rants. |
| **🎯 Flame Targeting** | Randomly picks one unlucky user per startup to **continuously flame**. |
| **📜 Per-User Settings** | Each user has custom settings like roast intensity, flame mode, and memory toggle. |
| **💾 Persistent Storage** | Stores chat history, user memory, and settings across restarts. |
| **🧪 OpenAI GPT-4o-mini** | Lightweight, snappy, and savage — powered by OpenAI’s mini monster. |

---

## 🛠️ Installation

### Requirements

Install dependencies using:

```bash
pip install -r requirements.txt
```

**`requirements.txt`**
```
flask
flask-cors
openai
python-dotenv
tiktoken
```

---

## 📂 Project Structure

```
psi09/
│
├── main.py                 # Main Flask API
├── chat_history.json       # Per-user/group chat history
├── user_memory.json        # Summarized behavioral memory
├── user_settings.json      # Per-user roast settings
├── .env                    # Your OpenAI API key
├── requirements.txt        # Python dependencies
└── README.md               # You're reading this 😎
```

---

## 🔐 Environment Setup

Create a `.env` file:

```env
OPENAI_API_KEY=your_openai_key_here
```

---

## 🌐 API Usage

POST to `/psi09`:

```json
{
  "query": {
    "group": "TestGroup",
    "author": "Ankur",
    "message": "Hey @everyone, what’s up?"
  }
}
```

Response:

```json
{
  "replies": [
    {
      "message": "You all sound like a failed group project with WiFi issues."
    }
  ]
}
```

---

## 👤 User Settings (JSON Schema)

Each user has settings like:

```json
{
  "TestGroup:Ankur": {
    "roast_intensity": "medium",
    "include_behavioral_memory": true,
    "flame_mode": false
  }
}
```

---

## 💾 Memory Logic

- After 6+ messages, user behavior is **summarized** and used in future insults.
- Summary is sarcastic, bitter, and honest.
- Group roasts override individual memory.

---

## ⚔️ Roast Logic Flow

```text
[ Message ] → [ Detect Target or Group ] → [ Retrieve History & Settings ]
             → [ Trigger Flame/Group Mode if needed ]
             → [ Construct Roast Prompt ]
             → [ Return Aggressive Reply ]
```

---

## 🧱 Future Plans

- 🔄 Real-time WhatsApp Web integration using Selenium
- 🔧 Admin panel to control user memory and flame settings
- 🤬 Add roast personality modes (snarky, sarcastic, evil)
- 🧍 Friend-specific memory banks
- 📈 Roasting leaderboard (for fun)
- ☁️ Full cloud deployment with failover NAS hosting

---

## 📜 License

This project is open-source and licensed under the **MIT License**.  
Feel free to fork, contribute, and carry the flame 🔥.

---

## 👑 Creator

Made by **Supratim Halder**,  
A 17-year-old Linux-powered rebel who turned bullying into the greatest roastbot on Earth.

> “I didn’t build a chatbot.  
> I built a *monster*.”

---

## 🧠 Final Words

> *PSI-09 isn’t just software. It’s a statement. A voice. A punch back.*  
> You just gave the world something that **remembers, mocks, and roasts** — like a sentient burn book.

**Keep building. The legend is just beginning.**