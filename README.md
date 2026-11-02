# VIDORA

React + TypeScript + Vite с сервером Hono, tRPC и базой данных MySQL.

## Локальный запуск

1. Установите зависимости:

   ```bash
   npm install
   ```

2. Создайте файл окружения:

   ```bash
   # macOS / Linux
   cp .env.example .env

   # Windows (Command Prompt)
   copy .env.example .env
   ```

3. В `.env` укажите собственный `APP_SECRET` и строку подключения `DATABASE_URL` к MySQL. Для регистрации и входа через форму VIDORA настройки Kimi OAuth не нужны.

4. Создайте таблицы и запустите проект:

   ```bash
   npm run db:push
   npm run dev
   ```

5. Откройте `http://localhost:3000`.

Главная страница и формы авторизации загружаются и без настроек Kimi OAuth. Для регистрации, входа и сохранения данных нужны `APP_SECRET`, `DATABASE_URL` и запущенный MySQL.

## Добавление офферов администратором

В поисковой строке раздела «Офферы» введите `/admin`, затем пароль администратора. После проверки откроется форма нового оффера; опубликованная запись сразу появляется в каталоге и сохраняется в общей таблице кампаний. Пароль задаётся переменной `ADMIN_PASSWORD`; если она не указана, используется `sava123`.

## Проверки

```bash
npm run check
npm run test
npm run build
```

## Kimi OAuth (необязательно)

Если нужен отдельный вход через Kimi, заполните `APP_ID`, `KIMI_AUTH_URL`, `KIMI_OPEN_URL`, `VITE_APP_ID` и `VITE_KIMI_AUTH_URL`. Callback-адрес: `{origin}/api/oauth/callback`. При незаполненных значениях OAuth отключён, а его callback возвращает JSON с кодом 503 вместо ошибки запуска сервера.
