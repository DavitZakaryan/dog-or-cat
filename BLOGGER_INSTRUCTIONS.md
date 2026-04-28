Как опубликовать `pet-quiz-multilang.html` в Google Blogger

1) Рекомендуемый способ: опубликовать как отдельную страницу (не пост)

- Открой Blogger → Страницы → Новая страница → вид HTML.
- Скопируй весь код из `pet-quiz-multilang.html` и вставь в HTML-редактор.

Важно: Blogger может удалять теги <script> из тела постов. Надёжнее использовать «Страницу», виджет «HTML/JavaScript» в Макете или разместить файл на внешнем хостинге (GitHub Pages).

2) Лучшая практика: разместить файл на GitHub Pages или другом статическом хостинге, а в Blogger добавить ссылку

- Закоммить `pet-quiz-multilang.html` в репозиторий GitHub и включить GitHub Pages (ветка gh-pages или папка /docs/).
- Укажи канонический URL в теге <head> файла (замени canonical href и og:image):

  <link rel="canonical" href="https://твойдомен.com/pet-quiz-multilang.html" />
  <meta property="og:image" content="https://твойдомен.com/путь/к/social-image.png" />

- В Blogger создай Страницу и добавь ссылку или iframe. Пример адаптивного iframe:

  <div style="position:relative;padding-top:56.25%;">
    <iframe src="https://твойдомен.com/pet-quiz-multilang.html" style="position:absolute;inset:0;border:0;width:100%;height:100%;"></iframe>
  </div>

3) Если нужно вставить HTML прямо в редактор поста / страницы Blogger

- Используй вид HTML и вставь только содержимое <body> (без тегов <html>, <head>, <body>, если Blogger их убирает).
- Скрипты перенеси в виджет: Blogger → Макет → Добавить гаджет → HTML/JavaScript. Убедись, что ID элементов в скрипте совпадают.

4) SEO и hreflang

- Файл уже динамически генерирует теги `link rel=alternate hreflang` и canonical. Для стабильного URL лучше прописать canonical вручную в <head>.
- Для лучшей индексации по языкам создай отдельные URL для каждого языка (например, `?lang=es` или `/ru/quiz.html`) и настрой серверные hreflang-теги. Blogger позволяет создать несколько страниц с canonical/hreflang.

5) Open Graph / Социальная картинка

- Создай PNG-изображение 1200×630 пикселей с заголовком «Кот или Собака?» и разместит его по стабильному URL. Укажи этот URL в `og:image` и `twitter:image` для красивых превью в соцсетях.

6) Доступность и производительность

- В файле уже есть ARIA-атрибуты и семантические теги `<main>` с `role`.
- Сжимай изображения, не злоупотребляй тяжёлыми анимациями на мобильных устройствах.

7) Тестирование локально

- Для корректной работы `URL()` в JS запусти локальный HTTP-сервер:

  python3 -m http.server 8000

  Затем открой: http://localhost:8000/pet-quiz-multilang.html

8) Финальный чек-лист перед публикацией

- Обнови `link[rel=canonical]` и `og:image` на финальные URL.
- При внешнем хостинге убедись, что CORS и заголовки настроены правильно (если встраиваешь через iframe).
- Проверь, что `robots.txt` и настройки сайта разрешают индексацию.
- Проверь разметку: используй Google Rich Results Test (https://search.google.com/test/rich-results) и инструмент проверки URL в Search Console.

Если хочешь, я могу:
- Создать шаблон social-preview изображения и добавить его в репозиторий.
- Настроить ветку GitHub Pages, запушить файл и дать тебе готовый URL.
- Подготовить отдельные страницы для каждого языка (например, `/es/`, `/ru/`) и обновить hreflang-теги.

Напиши, что делаем дальше.