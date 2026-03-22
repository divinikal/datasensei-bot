# DataSensei Bot

Adaptive data analysis practice bot for Telegram. Covers SQL, Python (Pandas/NumPy), Excel/Power BI, and Statistics & Probability. Difficulty adjusts automatically based on your performance.

-----

## Commands

|Command |Action                     |
|--------|---------------------------|
|/start  |Fresh session, resets score|
|/next   |Next challenge             |
|/quiz   |Quiz question              |
|/dataset|Mini dataset task          |
|/code   |Code challenge or review   |
|/skip   |Skip current challenge     |
|/score  |See your stats             |
|/sql    |Practice SQL               |
|/python |Practice Python/Pandas     |
|/excel  |Practice Excel/Power BI    |
|/stats  |Practice Statistics        |
|/help   |Show commands              |

Just type your answer or paste code at any time — no command needed.

-----

## Deploy on Railway (phone-friendly)

### 1. Get your keys

**Telegram Bot Token**

1. Open Telegram → message @BotFather
1. Send /newbot → follow prompts → copy the token

**Anthropic API Key**

- Go to console.anthropic.com → API Keys → Create key

-----

### 2. Put files on GitHub

Go to github.com → New repository → name it `datasensei-bot` → create these files one by one (tap Add file → Create new file):

```
bot.py
requirements.txt
Procfile
railway.toml
runtime.txt
.gitignore
README.md
```

-----

### 3. Deploy on Railway

1. Go to railway.app → sign up with GitHub
1. New Project → Deploy from GitHub repo → select `datasensei-bot`
1. Go to Variables tab → add:

```
TELEGRAM_BOT_TOKEN   =   your_telegram_token
ANTHROPIC_API_KEY    =   your_anthropic_key
```

1. Hit Deploy → check the Logs tab for: `DataSensei bot is running...`

Done — bot runs 24/7. Railway free tier ($5/month credit) is enough for personal use.

-----

## Run locally (optional)

```bash
pip install -r requirements.txt

export TELEGRAM_BOT_TOKEN="your_token"
export ANTHROPIC_API_KEY="your_key"

python bot.py
```

-----

## Notes

- State is in-memory — restarting the bot resets all scores. For persistence across restarts, the `context.bot_data` store can be swapped for a SQLite DB.
- Conversation history is capped at 30 turns per user to keep API costs low.
- Uses `claude-sonnet-4-20250514` for adaptive responses.

-----

## License

No restrictions — this code is yours. Third-party terms that apply:

- Telegram Bot API ToS: telegram.org/tos
- Anthropic Usage Policy: anthropic.com/legal/usage-policy
