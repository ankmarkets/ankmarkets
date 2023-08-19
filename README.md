from telegram import Update
from telegram.ext import Updater, CommandHandler, CallbackContext

# Funzione da eseguire quando il comando /start viene inviato al bot
def start(update: Update, context: CallbackContext) -> None:
    user = update.message.from_user
    update.message.reply_text(f"Ciao {user.first_name}! Benvenuto nel tuo bot.")

# Funzione da eseguire quando viene inviato il messaggio "plans"
def plans(update: Update, context: CallbackContext) -> None:
    update.message.reply_text("Ciao! Questo è il tuo bot. Sto rispondendo alla domanda 'plans'.")

# Funzione da eseguire quando viene inviato il messaggio "status"
def status(update: Update, context: CallbackContext) -> None:
    update.message.reply_text("Eccomi! Questo è il tuo bot. Sto rispondendo alla domanda 'status'.")

def main():
    # Inserisci qui il token del tuo bot ottenuto da BotFather
    bot_token = "6582853199:AAHplFxE6Ayvp3a-osCYPTqD-e-K5ZYOOeo"

    # Crea l'oggetto Updater e passa il token del bot
    updater = Updater(token=bot_token, use_context=True)

    # Ottieni il dispatcher per registrare comandi
    dispatcher = updater.dispatcher

    # Registra i gestori dei comandi
    dispatcher.add_handler(CommandHandler("start", start))
    dispatcher.add_handler(CommandHandler("plans", plans))  # Aggiunto il gestore per il comando /plans
    dispatcher.add_handler(CommandHandler("status", status))  # Aggiunto il gestore per il comando /status

    # Avvia il bot
    updater.start_polling()

    # Aggiorna fino a quando Ctrl+C non viene premuto
    updater.idle()

if __name__ == "__main__":
    main()
