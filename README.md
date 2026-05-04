# BabelFish

Голосовий AI-асистент у браузері. Приймає голосові запити від користувача, транскрибує їх у текст, обробляє через WatsonX та відповідає голосом.

---

## Як це працює

```
Мікрофон → Speech-to-Text → WatsonX LLM → Text-to-Speech → Динамік
```

1. Користувач натискає кнопку і говорить
2. Аудіо відправляється на сервер і транскрибується через Watson Speech-to-Text
3. Текст обробляється моделлю WatsonX
4. Відповідь перетворюється на голос і відтворюється у браузері

---

## Технології

| Компонент | Технологія |
|---|---|
| Бекенд | Python / Flask |
| Speech-to-Text | IBM Watson STT |
| Text-to-Speech | IBM Watson TTS |
| LLM | IBM WatsonX |
| Фронтенд | HTML + JavaScript (MediaRecorder API) |
| Контейнеризація | Docker |

---

## Структура проекту

```
server.py       # Flask-сервер, маршрути /speech-to-text, /text-to-speech, /watsonx
worker.py       # функції для роботи з Watson API
templates/      # HTML-інтерфейс
static/         # стилі та скрипти фронтенду
models/         # допоміжні моделі даних
```

---

## Запуск

```bash
# Через Docker
docker build -t babelfish .
docker run -p 5000:5000 babelfish

# Або локально
pip install -r requirements.txt
python server.py
```

Необхідні змінні середовища:
```env
WATSON_STT_KEY=ваш_ключ
WATSON_TTS_KEY=ваш_ключ
WATSONX_API_KEY=ваш_ключ
WATSONX_PROJECT_ID=ваш_project_id
```
