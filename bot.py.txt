import asyncio
from aiogram import Bot, Dispatcher
from aiogram.types import Message, ContentType

# Твой токен
TOKEN = "8431323424:AAFh84lXTjiNJAXvqXMhW43up2fbPdbSaVE"

# Создаем объекты бота и диспетчера
bot = Bot(token=TOKEN)
dp = Dispatcher()

# Обработчик команды /start
@dp.message(commands=["start"])
async def start_handler(message: Message):
    await message.answer("Привет! Я твой бот на aiogram 3.x 🚀")

# Обработчик любого текста
@dp.message()
async def echo_handler(message: Message):
    await message.answer(f"Ты написал: {message.text}")

# Запуск бота
async def main():
    await dp.start_polling(bot)

if __name__ == "__main__":
    asyncio.run(main())
