# SN Shop + Support

Готовый Telegram WebApp магазин с 4 витринами, кабинетом продавца и отдельной техподдержкой.

## Что внутри
- 4 магазина: TripShop, LimbPL, TripToys, TripChinaShop
- кабинет продавца
- быстрые роли через бота
- техподдержка с анкетой и отдельным чатом
- второй support-бот для уведомлений поддержки
- загрузка фото товара через Supabase Storage

## Как создать второго бота техподдержки
1. Открой BotFather
2. `/newbot`
3. Назови его например `SN Shop Support`
4. Скопируй токен
5. Вставь его в `SUPPORT_BOT_TOKEN`

## ENV
Скопируй `.env.example` в `.env`.

```env
BOT_TOKEN=токен_основного_бота
SUPPORT_BOT_TOKEN=токен_бота_поддержки
BASE_URL=https://твоя-ссылка.onrender.com
ADMIN_USERNAMES=твойusername
PORT=10000
STORAGE_MODE=supabase
SUPABASE_URL=https://project.supabase.co
SUPABASE_SERVICE_ROLE_KEY=sb_secret_xxx
SUPABASE_BUCKET=sn-shop
```

## Supabase
1. Создай project
2. Storage -> Create bucket -> `sn-shop`
3. Сделай bucket public
4. Возьми `SUPABASE_URL`
5. Возьми `Secret key (sb_secret...)`

## Render
Build command:
```bash
npm install
```

Start command:
```bash
npm start
```

Переменные окружения: те же, что в `.env`.

## Быстрые роли через основной бот
- `/seller_add @username`
- `/support_add @username`
- `/role @username seller`
- `/role @username support`
- `/unrole @username seller`
- `/unrole @username support`
- `/roles`

## Как работает поддержка
1. Пользователь жмёт `Техподдержка`
2. Заполняет анкету: Ник, проблема, дата, раздел
3. Создаётся отдельный чат в WebApp
4. Всем support-ролям, которые запустили второй бот, приходит анкета
5. Они нажимают `Принять` или `Игнорировать`
6. После принятия открывают чат и отвечают из веб-приложения

## Важно
Support-агент должен один раз нажать `/start` во втором support-боте, чтобы бот запомнил его chat id и мог присылать новые заявки.
