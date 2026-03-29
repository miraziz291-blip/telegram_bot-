 telegram_bot-
#
время импорта
импорт ос
импорт резьбы
из колбы импорт Фласк

ТОКЕН = os.environ.get("TELEGRAM_TOKEN")
OPENAI_API_KEY = os.environ.get("OPENAI_API_KEY")

Бот = телебот. TeleBot (TOKEN)
клиент = OpenAI(api_key=OPENAI_API_KEY)

PROMO_CODE = "miraziz+moxina=♥︎"
ЕЖЕДНЕВНЫЙ_ЛИМИТ = ПЯТЬ

пользователи = {}

def get_user(user_id):
 теперь = int(time.time()) 
 если user_id не в пользователях: 
 пользователи [user_id] = {"count": 0, "последний": теперь, "промо": Ложный, "платный_поколение": 0}
 элиф сейчас - пользователи [user_id]["последний"]  > 86400:
 пользователи [user_id]["счет"]  = 0
 пользователи [user_id]["последний"] = сейчас
 возвращайте пользователей [user_id]

def can_generate(user_id):
 пользователь = get_user(user_id) 
 если пользователь ["Промо"]: Вернись Истина
 если пользователь ["платные поколения"] > 0: Вернуть Истину
 если пользователь ["count"] < DAILY_LIMIT: Вернись Правда
 Ответ ложный 

def use_generation(user_id):
 пользователь = get_user(user_id) 
 если пользователь ["платные поколения"]  > 0:
 пользователь ["платные поколения"]  -= 1
 elif не пользователь ["Промо"]:
 пользователь ["count"]  += 1

@bot.message_handler(команды=["Начни"])
def start(сообщение):
 bot.send_message(message.chat.id, 
         "👋 Привет! Я AI-бот на базе ChatGPT.\n\n" 
         "📋 Команды:\n" 
         "/promo — ввести промокод\n" 
         "/buy — купить генерации за звёзды ⭐\n" 
         "/status — мой лимит\n\n" 
         "💬 Просто напиши мне сообщение — я отвечу!") 

@bot.message_handler(команды=["Статус"])











def status (согласно согласующимся):
 пользователь = get_user(message.chat.id) 
 если пользователь ["Промо"]:
         bot.send_message(message.chat.id, "✅ У тебя безлимитный доступ (промокод активирован).") 
 другое: 
 остаётся = DAILY_LIMIT - пользователь ["count"]
 bot.send_message(message.chat.id, 
             f"📊 Бесплатных генераций сег# telegram_bot- 
