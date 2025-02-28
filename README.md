# BackSpace – Телеграм-бот для рекомендаций фильмов

BackSpace – это Telegram-бот, который помогает пользователям находить интересные фильмы на основе их описания или тегов. Бот использует современную семантическую модель для поиска фильмов в базе данных и предоставляет дополнительные возможности, такие как отметка фильма как «просмотрено», оценка фильмов, добавление в список рекомендаций и многое другое.

---

## Функционал

- **Рекомендации фильмов:**  
  Бот анализирует введённое пользователем описание или теги и с помощью семантической модели находит 3 наиболее релевантных фильма из базы данных.

- **Семантический поиск:**  
  Для оценки схожести между запросом пользователя и фильмами в базе используется модель [SentenceTransformer](https://www.sbert.net/), конкретно — модель `sberbank-ai/sbert_large_nlu_ru`. Она кодирует текст запроса в векторное представление, после чего происходит вычисление косинусного сходства с эмбеддингами фильмов.

- **Работа с базой данных:**  
  - **movies.db:** Хранит информацию о фильмах, включая название, рейтинг, страну, жанр, год выпуска, продолжительность, режиссёра, актёров, теги, описание и эмбеддинги (для двух вариантов поиска – по описанию и по тегам).
  - **user.db:** Сохраняет данные о фильмах, выбранных пользователями – статус «просмотрено», оценки и прочее.
  - **rec.db:** Отвечает за хранение предпочтений пользователей, которые используются для формирования рекомендаций.

- **Дополнительный функционал:**  
  - Отметка фильма как просмотренного.
  - Оценка фильма пользователем.
  - Добавление фильма в список рекомендаций.
  - Просмотр списка просмотренных фильмов и фильмов с оценками.
  - Интерактивное управление через inline-клавиатуры.

- **Парсинг базы данных:**  
  Вся информация для базы фильмов была собрана и распарсена самостоятельно с помощью файла `parse.py`. Этот скрипт отвечает за сбор, обработку и запись данных о фильмах (включая вычисление эмбеддингов) в базу `movies.db`.

---

## Технологический стек

- **Язык программирования:** Python
- **Фреймворк для Telegram-ботов:** [aiogram](https://docs.aiogram.dev/)
- **Базы данных:** SQLite (с файлами `movies.db`, `user.db` и `rec.db`)
- **Асинхронная работа с БД:** [aiosqlite](https://aiosqlite.omnilib.dev/)
- **Математические вычисления:** NumPy
- **Семантическая модель:** [SentenceTransformer](https://www.sbert.net/) (модель `sberbank-ai/sbert_large_nlu_ru`)

---

## Установка и запуск

1. **Клонируйте репозиторий:**

   ```bash
   git clone https://github.com/yourusername/backspace-bot.git
   cd backspace-bot

