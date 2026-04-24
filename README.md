# Asistente de Documentos con Gemini y Gradio

Aplicación de chat que responde preguntas sobre el paper **"Attention is All You Need" (Vaswani et al., 2017)** basándose exclusivamente en el contenido del PDF, sin recurrir a conocimiento externo del modelo.

## ¿Qué hace?

Extrae el texto completo del paper, lo inyecta en el system prompt de Gemini y construye una interfaz de chat con Gradio. El modelo solo puede responder con información presente en el documento.

Esta técnica es la base conceptual de **RAG (Retrieval-Augmented Generation)**.

## Tecnologías

- `pypdf` — extracción de texto desde PDF
- `google-genai` — cliente de la API de Gemini
- `gradio` — interfaz web de chat
- `python-dotenv` — manejo de credenciales

## Instalación

```bash
pip install -r requirements.txt
```

## Configuración

Crea un archivo `.env` en la raíz del proyecto con tu API key de Gemini:

```
GEMINI_API_KEY="tu_api_key_aqui"
```

Puedes obtener una key gratuita en [aistudio.google.com](https://aistudio.google.com).

## Uso

1. Descarga el paper desde ArXiv (la primera celda lo hace automáticamente):
   ```
   https://arxiv.org/pdf/1706.03762
   ```

2. Ejecuta las celdas del notebook en orden.

3. La última celda lanza la interfaz. En Colab usa:
   ```python
   demo.launch(share=True) #Añadimos debug=True por si ocurria un error mientras mandabamos preguntas
   ```

## Estructura del proyecto

```
├── 05_ejercicio__1_.ipynb   # Notebook principal
├── requirements.txt         
└── attention_is_all_you_need.pdf  # Se descarga automáticamente
```

## Limitaciones

Este enfoque inyecta el documento completo en el contexto del modelo en cada llamada. Funciona bien para documentos cortos (el paper tiene ~39,630 caracteres), pero no escala a documentos de cientos de páginas. Para eso existe RAG.

## Referencia

Vaswani, A. et al. (2017). *Attention is All You Need*. [arxiv.org/abs/1706.03762](https://arxiv.org/abs/1706.03762)
