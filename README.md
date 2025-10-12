# 🎬 Mini App для показа рекламы

## 📋 Что это?

Это Web App страница для показа рекламы перед фильмами/сериалами в Telegram боте.

## 🚀 Как разместить страницу?

### Вариант 1: GitHub Pages (БЕСПЛАТНО, РЕКОМЕНДУЕТСЯ)

1. **Создайте репозиторий на GitHub:**
   - Зайдите на https://github.com
   - Нажмите "New repository"
   - Назовите, например: `telegram-bot-ads`
   - Сделайте публичным (Public)

2. **Загрузите файл `ad_page.html`:**
   - Откройте репозиторий
   - Нажмите "Add file" → "Upload files"
   - Загрузите файл `ad_page.html`

3. **Включите GitHub Pages:**
   - Зайдите в Settings → Pages
   - Source: выберите "main branch"
   - Сохраните

4. **Получите ссылку:**
   - Ваша страница будет доступна по адресу:
   - `https://ваш-username.github.io/telegram-bot-ads/ad_page.html`

### Вариант 2: Vercel (БЕСПЛАТНО)

1. Зайдите на https://vercel.com
2. Импортируйте репозиторий из GitHub
3. Deploy
4. Получите ссылку: `https://your-project.vercel.app/ad_page.html`

### Вариант 3: Netlify (БЕСПЛАТНО)

1. Зайдите на https://www.netlify.com
2. Drag & drop папку `web_app`
3. Получите ссылку: `https://your-site.netlify.app/ad_page.html`

---

## 💰 Как подключить рекламу?

### Google AdSense

1. Зарегистрируйтесь на https://www.google.com/adsense
2. Добавьте ваш сайт (ссылку GitHub Pages)
3. Получите код рекламы
4. Вставьте в `ad_page.html` вместо комментария `<!-- ПРИМЕР: Код Google AdSense -->`

### PropellerAds (легче всего)

1. Зарегистрируйтесь на https://propellerads.com
2. Создайте новую зону (Zone)
3. Получите JavaScript код
4. Вставьте в блок `<div class="ad-container">`

### Yandex.Direct

1. Зарегистрируйтесь на https://direct.yandex.ru
2. Создайте рекламную кампанию
3. Получите код баннера
4. Вставьте в HTML

---

## 🔧 Интеграция в бота

После размещения страницы, добавьте в `config.py`:

```python
# URL вашего Mini App
WEB_APP_URL = "https://ваш-username.github.io/telegram-bot-ads/ad_page.html"
```

И используйте в боте:

```python
from aiogram.types import WebAppInfo, InlineKeyboardButton, InlineKeyboardMarkup

keyboard = InlineKeyboardMarkup(inline_keyboard=[
    [InlineKeyboardButton(
        text="📺 Смотреть с рекламой", 
        web_app=WebAppInfo(url=f"{WEB_APP_URL}?movie={movie_key}&type=movie")
    )],
    [InlineKeyboardButton(
        text="💎 Премиум (без рекламы)", 
        callback_data=f"premium_{movie_key}"
    )]
])
```

---

## ⚙️ Настройки таймера

В файле `ad_page.html` найдите строку:

```javascript
const TIMER_SECONDS = 10; // Время показа рекламы в секундах
```

Измените `10` на нужное количество секунд (рекомендуется 5-15 секунд).

---

## 📊 Статистика

Страница автоматически отправляет данные боту после просмотра рекламы:
- `content_key` - ключ фильма/сериала
- `content_type` - тип контента (movie/series)
- `timestamp` - время просмотра

Эти данные можно использовать для аналитики.

---

## 🎨 Кастомизация

Вы можете изменить:
- Цвета (градиенты в CSS)
- Текст сообщений
- Время таймера
- Дизайн кнопок

Все настройки в файле `ad_page.html`.

---

## ❓ FAQ

**Q: Сколько можно заработать?**
A: $0.50-$3 за 1000 просмотров (зависит от рекламной сети и региона)

**Q: Нужен ли домен?**
A: Нет, можно использовать бесплатные GitHub Pages

**Q: Какая рекламная сеть лучше?**
A: PropellerAds - проще всего начать, Google AdSense - больше доход

**Q: Можно ли пропустить рекламу?**
A: Нет, кнопка появляется только после таймера

---

## 📞 Поддержка

Если возникли вопросы - напишите в чат!
