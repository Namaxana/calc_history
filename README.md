# 🤖 Калькулятор — Telegram Mini App

## Что это
Telegram Mini App калькулятор с **общей историей вычислений** для всех пользователей.

---

## 📁 Файлы
- `calculator_miniapp.html` — весь фронтенд (один файл)

---

## 🚀 Деплой: шаг за шагом

### 1. Разместить HTML-файл на хостинге

Вариант A — **GitHub Pages** (бесплатно):
1. Создай репозиторий на github.com
2. Залей `calculator_miniapp.html` как `index.html`
3. Settings → Pages → Source: main / root
4. Твой URL: `https://USERNAME.github.io/REPO/`

Вариант B — **Netlify** (бесплатно, 1 минута):
1. Зайди на netlify.com
2. Drag & drop файл `calculator_miniapp.html`
3. Получи URL вида `https://random-name.netlify.app`

> ⚠️ Обязателен HTTPS!

---

### 2. Создать бота через @BotFather

```
/newbot
→ Введи название: My Calc Bot
→ Введи username: my_calc_bot
→ Получи токен: 123456:ABC-DEF...
```

---

### 3. Создать Mini App в @BotFather

```
/newapp
→ Выбери своего бота
→ Название: Калькулятор
→ Описание: Умный калькулятор с общей историей
→ Фото: загрузи любую иконку (640x360 px)
→ GIF: пропусти (Send /empty)
→ URL: вставь свой HTTPS-адрес из шага 1
→ Short name: calc
```

---

### 4. Добавить кнопку в бот (необязательно)

Простой Python бот с кнопкой запуска:

```python
pip install python-telegram-bot

# bot.py
from telegram import Update, WebAppInfo, InlineKeyboardButton, InlineKeyboardMarkup
from telegram.ext import ApplicationBuilder, CommandHandler, ContextTypes

TOKEN = "ВАШ_ТОКЕН"
APP_URL = "https://ВАШ_САЙТ/"

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    kb = [[InlineKeyboardButton(
        "🧮 Открыть калькулятор",
        web_app=WebAppInfo(url=APP_URL)
    )]]
    await update.message.reply_text(
        "Привет! Нажми кнопку, чтобы открыть калькулятор с общей историей.",
        reply_markup=InlineKeyboardMarkup(kb)
    )

app = ApplicationBuilder().token(TOKEN).build()
app.add_handler(CommandHandler("start", start))
app.run_polling()
```

Запуск: `python bot.py`

---

## ✨ Функции

| Функция | Описание |
|---|---|
| Калькулятор | Полноценный с поддержкой +, −, ×, ÷, %, +/− |
| История | Общая для ВСЕХ пользователей (shared storage) |
| Имя пользователя | Показывает кто из пользователей сделал вычисление |
| Тап по истории | Копирует результат обратно в калькулятор |
| Клавиатура | Поддержка физической клавиатуры |
| Очистка | Кнопка очистки всей истории |

---

## 🔧 Настройки

В файле `calculator_miniapp.html` можно изменить:
- `MAX_ITEMS = 100` — сколько записей хранить в истории
- Цвета через CSS переменные `:root { --accent: ... }`
