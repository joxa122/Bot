from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler

# "/start" komandasi uchun funksiya
async def start(update: Update, context):
    await update.message.reply_text("Salom! Mana sizga musiqa:")
    # Musiqa faylini yuborish
    with open("music.mp3", "rb") as music:
        await update.message.reply_audio(audio=music)

# Botni ishga tushirish
async def main():
    token = "6562627300:AAGItGJFa3u7i99ySSCSsir7YCmr0GmQJiM"  # Bu yerga BotFatherdan olingan tokenni kiriting
    app = ApplicationBuilder().token(token).build()

    app.add_handler(CommandHandler("start", start))

    print("Bot ishlamoqda...")
    await app.run_polling()

if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
