# 🤖 SmartBot AI Assistant

A modern, full-stack **Rule-Based AI Chatbot** built with Python (Flask), SQLite, HTML5, CSS3, and Vanilla JavaScript.

---

## 📸 Features

| Feature | Details |
|---|---|
| **Chatbot Engine** | Rule-based logic with nested conditions |
| **Personality** | Professional, friendly, educational |
| **Topics** | Programming, AI/ML, Web Dev, Databases, Career, Jokes, Quotes |
| **UI** | Modern ChatGPT-like interface with dark mode |
| **Database** | SQLite — stores all chat history with timestamps |
| **Admin Panel** | Dashboard with analytics, search, and conversation viewer |
| **Extras** | Download chat as TXT, clear chat, typing animation, auto-scroll |

---

## 🗂 Project Structure

```
smartbot/
├── app.py              # Flask application & API routes
├── chatbot.py          # Rule-based chatbot engine
├── database.db         # SQLite database (auto-created)
├── requirements.txt    # Python dependencies
│
├── templates/
│   ├── index.html      # Main chat interface
│   └── admin.html      # Admin dashboard
│
├── static/
│   ├── css/
│   │   └── style.css   # Complete stylesheet
│   └── js/
│       ├── script.js   # Chat interface logic
│       └── admin.js    # Admin dashboard logic
│
└── README.md
```

---

## 🚀 Installation & Setup

### Prerequisites
- Python 3.8+
- pip

### Steps
✅ Step 1 — Check Python is Installed
Open your terminal (Command Prompt / PowerShell on Windows, Terminal on Mac/Linux) and run:

python --version

You need Python 3.8 or higher. If not installed, download from python.org.

✅ Step 2 — Extract the ZIP File

Download the SmartBot_AI_Assistant.zip file

You'll get a folder called smartbot/


✅ Step 3 — Open Terminal in the Project Folder
Windows:

Open the smartbot folder in File Explorer
Click the address bar, type cmd, press Enter


dir       # Windows


You should see: app.py, chatbot.py, requirements.txt, templates/, static/

✅ Step 4 — Create a Virtual Environment (Recommended)

python -m venv venv

# Activate it
# Windows:
venv\Scripts\activate


✅ Step 5 — Install Dependencies


pip install -r requirements.txt


This installs Flask. You'll see output like Successfully installed flask-3.x.x.

✅ Step 6 — Run the Application


python app.py

### Access

| Page | URL |
|---|---|
| Chat Interface | http://127.0.0.1:5000 |
| Admin Dashboard | http://127.0.0.1:5000/admin |

---

## 🗄️ Database Schema

```sql
-- Conversations table
CREATE TABLE conversations (
    id          INTEGER PRIMARY KEY AUTOINCREMENT,
    session_id  TEXT NOT NULL,
    created_at  DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- Messages table
CREATE TABLE messages (
    id              INTEGER PRIMARY KEY AUTOINCREMENT,
    conversation_id INTEGER NOT NULL,
    sender          TEXT NOT NULL CHECK(sender IN ('user','bot')),
    content         TEXT NOT NULL,
    timestamp       DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (conversation_id) REFERENCES conversations(id)
);
```

---

## 💬 Chatbot Capabilities

### Greetings
- `hello`, `hi`, `hey`, `good morning`, `good evening`

### Identity
- "What's your name?", "Who made you?", "How old are you?"

### Technical Topics
| Topic | Subtopics |
|---|---|
| Programming | Python, Java, JavaScript, C++, Rust |
| AI & ML | Machine Learning, Deep Learning, NLP, Neural Networks, Chatbots |
| Web Dev | HTML/CSS, React, Flask, Django, Node.js |
| Databases | SQLite, MySQL, PostgreSQL, MongoDB |

### Career
- Internship advice, Resume/CV tips, Interview preparation

### Fun
- Jokes (8 curated programmer jokes)
- Motivational quotes (8 curated tech quotes)
- Current date & time
- Basic arithmetic (e.g. "calculate 25 * 4")

---

## 🔌 API Reference

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/chat` | Send message, get response |
| GET | `/api/history` | Fetch session history |
| GET | `/api/admin/stats` | Dashboard statistics |
| GET | `/api/admin/messages` | Paginated messages + search |
| GET | `/api/admin/conversation/<id>` | Single conversation |

### POST `/api/chat`
```json
// Request
{ "message": "Hello!", "session_id": "session_123" }

// Response
{ "response": "Good morning! 👋 ...", "timestamp": "2024-01-15 10:30:00", "status": "success" }
```

---

## 🎨 UI Features

- **Dark Mode** — toggle via sun/moon icon; preference persisted in localStorage
- **Typing Animation** — bouncing dots while bot "thinks"
- **Markdown Rendering** — bold, italic, code, lists rendered in bot messages
- **Auto-scroll** — always shows latest message
- **Suggestion Chips** — quick-start buttons on welcome screen
- **Mobile Responsive** — collapsible sidebar, touch-friendly
- **Clear Chat** — confirmation modal before clearing
- **Download Chat** — exports as timestamped `.txt` file

---

## 🛡️ Architecture

```
Browser (HTML/CSS/JS)
        │  POST /api/chat  │  GET /api/*
        ▼
Flask App (app.py)
        │
        ├── chatbot.py  ←  SmartBot rule engine
        │
        └── SQLite DB   ←  conversations + messages
```

---

## 🔮 Future Enhancements

1. **NLP Integration** — spaCy / NLTK for intent classification
2. **LLM Fallback** — use GPT/Gemini API when rules don't match
3. **User Authentication** — login/register for personal history
4. **Multi-language Support** — Urdu, Arabic, French responses
5. **Voice Input/Output** — Web Speech API integration
6. **Analytics Charts** — Chart.js visualizations in admin panel
7. **Webhook Integrations** — Slack, WhatsApp, Telegram bots
8. **Docker** — containerize for easy cloud deployment

---

## 📄 License

MIT — free for educational and personal use.

---

*Built with ❤️ using Python, Flask, SQLite, HTML5, CSS3, and Vanilla JavaScript*
