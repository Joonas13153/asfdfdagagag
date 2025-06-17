# Tööintervjuu AI Chatbot Backend

See on FastAPI-põhine taustsüsteem, mis kasutab OpenAI API-d tööintervjuu simulatsiooni jaoks.

## Failid

- `main.py` — FastAPI rakendus
- `requirements.txt` — vajalikud Python teegid
- `Dockerfile` — konteineriseerimine Dockeriga
- `README.md` — see juhend

## Paigaldus ja kasutamine

### 1. Paigalda sõltuvused

```bash
pip install -r requirements.txt
```

### 2. Määra oma OpenAI API võti keskkonnamuutujaks

```bash
export OPENAI_API_KEY="sk-xxxxxx"   # Linux/macOS
set OPENAI_API_KEY=sk-xxxxxx        # Windows CMD
```

### 3. Käivita lokaalselt

```bash
uvicorn main:app --reload
```

### 4. Või ehita ja käivita Dockeris

```bash
docker build -t intervjuu-chatbot .
docker run -p 8080:8080 -e OPENAI_API_KEY="sk-xxxxxx" intervjuu-chatbot
```

### 5. Deploy Fly.io-sse

```bash
fly launch
fly secrets set OPENAI_API_KEY="sk-xxxxxx"
fly deploy
```

## API lõpp-punkt

POST `/chat` — saadab sõnumi ja vestluse ajaloo ning saab vastuse.

