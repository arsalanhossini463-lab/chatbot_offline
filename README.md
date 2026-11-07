# Streamlit Ollama Chatbot

A simple chatbot web app built with [Streamlit](https://streamlit.io/) that talks to a local language model through [Ollama](https://ollama.com/). By default it uses the `gemma3:1b` model. Everything runs on your own computer, so no API key is needed.

## Features

- Chat interface with message history
- Streaming answers that appear word by word (`app_1.py`)
- **Clear History** button
- **Summarize & Save Chat** button: saves the conversation to `chat.txt` and a short AI summary to `summary.txt`

## Files

| File | Description |
|------|-------------|
| `app.py` | Basic chatbot. Waits for the full answer and shows a loading spinner. Uses `utils.py`. |
| `app_1.py` | Improved chatbot with streaming answers, a Stop button, Clear History and Summarize & Save Chat. Uses `utils_1.py`. |
| `utils.py` | `call_ollama_model()` sends a prompt to Ollama and returns the full answer. |
| `utils_1.py` | Same as `utils.py` plus `stream_ollama_model()`, which yields the answer piece by piece. |

## Requirements

- Python 3
- [Ollama](https://ollama.com/) installed and running
- The `gemma3:1b` model
- The packages in `requirements.txt`: `streamlit` and `requests`

## Installation

```bash
# Download the model (once)
ollama pull gemma3:1b

# Install the Python packages
pip install -r requirements.txt
```

## Usage

Make sure Ollama is running, then start one of the apps:

```bash
streamlit run app.py
# or the improved version
streamlit run app_1.py
```

Open the address shown in the terminal (usually `http://localhost:8501`).

You can also test the model from the terminal without Streamlit:

```bash
python utils.py
```

## Notes

- Ollama must be reachable at `http://localhost:11434` (its default address).
- To use another model, pull it with Ollama and change `model = "gemma3:1b"` in the code.
- `chat.txt` and `summary.txt` are created in the project folder when you press **Summarize & Save Chat**.
