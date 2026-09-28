```mermaid
graph TD
    subgraph Capa1 ["1. CAPA DE PRESENTACIÓN"]
        A[" Usuario / Cliente"] -->|Escribe consulta| B[" Interfaz Streamlit app.py"]
        B -->|Guarda historial| C[" st.session_state"]
    end

    subgraph Capa2 ["2. CAPA DE PROCESAMIENTO"]
        C -->|Pasa mensaje + Prompt| D["⚙️ Context Builder Prompt Engine"]
        D -->|Petición HTTP POST / JSON| E["🌐 API REST http://localhost:11434"]
    end

    subgraph Capa3 ["3. CAPA DE INFERENCIA IA"]
        E -->|Recibe request| F[" Servidor Local Ollama"]
        F -->|Procesa tokens| G[" Modelo Llama 3.2"]
    end

    subgraph Capa4 ["4. CAPA DE RETORNO Y SALIDA"]
        G -->|Devuelve respuesta| F
        F -->|Retorna JSON| E
        E -->|Renderiza mensaje| H[" Respuesta en Pantalla"]
    end
```

# Chat Bot Parrillero

Aplicación de Streamlit para recomendar el término ideal de cocción de carne según el corte solicitado.

## Requisitos

- Python 3.10+
- Ollama ejecutándose localmente
- Modelo `llama3.2:1b`

## Instalación

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
# En Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Ejecutar la app

```bash
streamlit run app.py
```

## Importante

La app envía peticiones a `http://localhost:11434/api/chat`, por lo que debes tener Ollama corriendo en tu equipo.

## Descripción

El chatbot responde con recomendaciones de cocción para cortes de carne, explica por qué se recomienda cada término y puede sugerir acompañamientos.
