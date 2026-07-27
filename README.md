## 🇸🇪 **Svensk version**


# ✦ Local NSFW Studio — Ollama + ComfyUI

En lokal, privat webbläsarbaserad studio för erotisk rollspel och bildgenerering. Den kombinerar **Ollama** (för chatt/LLM) med **ComfyUI** (för Stable Diffusion-bildgenerering). Allt körs lokalt i din webbläsare utan att data behöver skickas till molnet.

---

## 🚀 Snabbstart

### 1. Förbered miljö
Du behöver ha följande tjänster igång på din dator:

- **Ollama**: Installera och dra ner en chattmodell (t.ex. `https://huggingface.co/mradermacher/Qwen3.5-9B-heretic-GGUF` för vision och samma för text).
  ```bash
  ollama pull https://huggingface.co/HauhauCS/Qwen3.5-9B-Uncensored-HauhauCS-Aggressive:Q4_K_M
  ```

- **ComfyUI**: Dra ner och starta ComfyUI med en checkpoint (t.ex. `epicrealism.safetensors`).
  ```bash
  python main.py --enable-cors-header
  ```

### 2. Kör applikationen

Eftersom detta är en enda fil (`nsfw.html`) behöver du bara öppna den i din webbläsare, eller servera den lokalt:

```bash
# Med Python (rekommenderas för bästa upplevelse)
python -m http.server 8000
# Öppna sedan http://127.0.0.1:8000/nsfw.html i din webbläsare
```

### 3. Anslutning

| Inställning | Värde (Standard) |
|-------------|------------------|
| **Ollama URL** | `http://127.0.0.1:11434` |
| **ComfyUI URL** | `http://127.0.0.1:8188` |

Klicka på **"Testa Ollama"** och **"Testa ComfyUI"** för att verifiera anslutningen.

---

## ✨ Funktioner

| Funktion | Beskrivning |
| :--- | :--- |
| **Hybrid Workflow** | Chat med Ollama + Bildgenerering via ComfyUI i samma fönster. |
| **Vision Support** | Ladda upp eller klistra in bilder för analys (kräver vision-modell). |
| **Lokal & Privat** | Chathistoria och galleri sparas lokalt via IndexedDB. |
| **Tema-stöd** | Mörkt, Ljust, Synthwave eller Dracula-tema. |
| **Språkval** | Byt mellan Engelska (EN) och Svenska (SV). |
| **Kontextfönster** | Stort kontextfönster (131k tokens) för långare samtal. |

---

## 📜 Kommandon i chatten

Du kan använda följande kommandon direkt i chat-rutan:

- `/image [prompt]` → Skickar prompten direkt till ComfyUI (engelska rekommenderas).
- `/image tr [prompt]` → Översätter prompten först till engelska, sedan genererar.
- `/clear` → Rensar hela chattfönstret.
- `/system [text]` → Uppdaterar systemprompten (t.ex. för att ändra ton).

**Exempel:**
```text
/image en woman, 20 years old, wearing a red dress...
```

---

## ⚙️ Konfiguration & Inställningar

### System Prompt (Vänsterpanel)
Standardinställningen är anpassad för **18–20 år gamla** karaktärer. Du kan ändra tonen via "Persona / system"-sektionen:

- `Standard 18–20`
- `Romantik`
- `Explicit`
- `Maktspel (D/s)`

### Bildgenerering (ComfyUI)
Anpassa dina genereringar i panelen "Bildinställningar":

- **Quality Tags**: Välj mellan `masterpiece`, `cinematic`, etc.
- **Subject/Pose/Clothing**: Färdiga mallar för olika scenerier.
- **Sampler/Scheduler**: Justera `euler_ancestral` eller `dpmpp_sde`.

### Galleri & Avatars

- **Galleri**: Sparas lokalt, kan exporteras som JSON (`Exportera JSON`).
- **Avatars**: Ladda upp en profilbild för dig själv och AI:n (kommer ihåg efter omladdning).

---

## 💻 Tekniska Detaljer

| Kategori | Detalj |
| :--- | :--- |
| **Språk** | HTML5 / CSS3 / Vanilla JavaScript |
| **Lagring** | IndexedDB (för galleri, chatt och avatars) |
| **API** | Ollama (`/api/chat`), ComfyUI (`/prompt`, `/system_stats`) |
| **Kontext** | Max 131 072 tokens (justerbart i inställningar) |

---

## 📦 Struktur

```text
repo/
├── nsfw.html      # Huvudapplikationen
├── README.md      # Denna fil
└── serve.py       # (Valfritt) Python-skript för att servera HTML-filen
```

**Exempel på `serve.py`:**
```python
from http.server import SimpleHTTPRequestHandler, HTTPServer
import os

os.chdir(os.path.dirname(os.path.abspath(__file__)))

handler = SimpleHTTPRequestHandler
server_address = ('', 8000)
httpd = HTTPServer(server_address, handler)
print("Serving at http://127.0.0.1:8000")
httpd.serve_forever()
```

---

## 📄 Licens

Koden är öppen för ändring och delning. Användare ansvarar för hur de konfigurerar systemprompten (t.ex. explicit innehåll).

**Version:** 1.0  
**Datum:** 27 juli 2026
```

---

## 🇬🇧 **English version**

```markdown
# ✦ Local NSFW Studio — Ollama + ComfyUI

A local, private browser-based studio for erotic roleplay and image generation. It combines **Ollama** (for chat/LLM) with **ComfyUI** (for Stable Diffusion image generation). Everything runs locally in your browser without needing to send data to the cloud.

---

## 🚀 Quick Start

### 1. Prepare Environment
You need to have the following services running on your computer:

- **Ollama**: Install and pull a chat model (e.g., `https://huggingface.co/trohrbaugh/Qwen3.5-9B-heretic` for vision, same for text).
  ```bash
  ollama pull https://huggingface.co/HauhauCS/Qwen3.5-9B-Uncensored-HauhauCS-Aggressive:Q4_K_M
  ```

- **ComfyUI**: Download and start ComfyUI with a checkpoint (e.g., `epicrealism.safetensors`).
  ```bash
  python main.py --enable-cors-header
  ```

### 2. Run the Application

Since this is a single file (`nsfw.html`), you can just open it in your browser, or serve it locally:

```bash
# With Python (recommended for best experience)
python -m http.server 8000
# Then open http://127.0.0.1:8000/nsfw.html in your browser
```

### 3. Connection Settings

| Setting | Default Value |
|---------|---------------|
| **Ollama URL** | `http://127.0.0.1:11434` |
| **ComfyUI URL** | `http://127.0.0.1:8188` |

Click **"Test Ollama"** and **"Test ComfyUI"** to verify the connection.

---

## ✨ Features

| Feature | Description |
| :--- | :--- |
| **Hybrid Workflow** | Chat with Ollama + Image Generation via ComfyUI in the same window. |
| **Vision Support** | Upload or paste images for analysis (requires vision model). |
| **Local & Private** | Chat history and gallery saved locally via IndexedDB. |
| **Theme Support** | Dark, Light, Synthwave, or Dracula theme. |
| **Language Toggle** | Switch between English (EN) and Swedish (SV). |
| **Context Window** | Large context window (131k tokens) for longer conversations. |

---

## 📜 Chat Commands

You can use the following commands directly in the chat box:

- `/image [prompt]` → Sends prompt directly to ComfyUI (English recommended).
- `/image tr [prompt]` → Translates prompt to English first, then generates.
- `/clear` → Clears entire chat window.
- `/system [text]` → Updates system prompt (e.g., to change tone).

**Example:**
```text
/image en woman, 20 years old, wearing a red dress...
```

---

## ⚙️ Configuration & Settings

### System Prompt (Sidebar)
The default is tuned for **18–20 year old** characters. You can change the tone via the "Persona / system" section:

- `Standard 18–20`
- `Romance`
- `Explicit`
- `Power Play (D/s)`

### Image Generation (ComfyUI)
Customize your generations in the "Image Settings" panel:

- **Quality Tags**: Choose between `masterpiece`, `cinematic`, etc.
- **Subject/Pose/Clothing**: Ready-made templates for different scenarios.
- **Sampler/Scheduler**: Adjust `euler_ancestral` or `dpmpp_sde`.

### Gallery & Avatars

- **Gallery**: Saved locally, can be exported as JSON (`Export JSON`).
- **Avatars**: Upload a profile picture for yourself and the AI (remembers after reload).

---

## 💻 Technical Details

| Category | Detail |
| :--- | :--- |
| **Language** | HTML5 / CSS3 / Vanilla JavaScript |
| **Storage** | IndexedDB (for gallery, chat, and avatars) |
| **API** | Ollama (`/api/chat`), ComfyUI (`/prompt`, `/system_stats`) |
| **Context** | Max 131,072 tokens (adjustable in settings) |

---

## 📦 Structure

```text
repo/
├── nsfw.html      # Main application
├── README.md      # This file
└── serve.py       # (Optional) Python script to serve HTML file
```

**Example `serve.py`:**
```python
from http.server import SimpleHTTPRequestHandler, HTTPServer
import os

os.chdir(os.path.dirname(os.path.abspath(__file__)))

handler = SimpleHTTPRequestHandler
server_address = ('', 8000)
httpd = HTTPServer(server_address, handler)
print("Serving at http://127.0.0.1:8000")
httpd.serve_forever()
```

---

## 📄 License

The code is open for modification and sharing. Users are responsible for how they configure system prompts (e.g., explicit content).

**Version:** 1.0  
**Date:** July 27, 2026
```

---

## 💡 Tips för GitHub-repo

Om du ska ladda upp detta till GitHub:

1. Skapa en mapp `repo/` med filerna `nsfw.html`, `README.md` (svensk) och `README_en.md` (engelsk).
2. Lägg till `.gitignore` för att exkludera temporära filer.
3. Lägg till `LICENSE`-fil om du vill ha en licens.

**Exempel på `.gitignore`:**
```text
# Temporära filer
*.pyc
__pycache__/
.env

# Webbbläsarens cache
*.tmp
*.temp
```
