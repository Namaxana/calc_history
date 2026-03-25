import telebot

TOKEN = "8765574541:AAEc2QDe8W7C-5zaij_QalAHtzS8hqugXq0"

bot = telebot.TeleBot(TOKEN)

@bot.message_handler(commands=['start'])
def start(message):
    bot.send_message(message.chat.id, "Привет! Бот работает из одного файла на GitHub.")

@bot.message_handler(func=lambda m: True)
def echo(message):
    bot.send_message(message.chat.id, f"Ты написал: {message.text}")

bot.polling(none_stop=True)
