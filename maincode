from telegram import Update
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext
import requests
import json
import random

TOKEN = '6552849502:AAFoeXnZ8aW2wzQJAktyaRIGOQVSQDtiND8'

MOTS_CLES = ['blague', 'dad', 'papa']

def get_dad_joke():
    response = requests.get('https://icanhazdadjoke.com/', headers={'Accept': 'application/json'})
    data = json.loads(response.text)
    return data['joke']


def handle_message(update: Update, context: CallbackContext):
    user_input = update.message.text.lower()
    
    if any(keyword in user_input for keyword in MOTS_CLES):
        joke = get_dad_joke()
        update.message.reply_text(joke)

def main():
    updater = Updater(TOKEN, use_context=True)
    dispatcher = updater.dispatcher

    dispatcher.add_handler(MessageHandler(Filters.text & ~Filters.command, handle_message))

    updater.start_polling()
    updater.idle()

if __name__ == '__main__':
    main()
