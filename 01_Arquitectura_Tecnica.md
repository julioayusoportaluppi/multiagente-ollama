
# DIAGRAMA DE ARQUITECTURA
## Asistente empresarial inteligente

Este diagrama representa la arquitectura lógica del sistema.

```mermaid
flowchart TD
    U[Usuario] --> UI[Interfaz Web]
    UI --> API[Backend Python FastAPI]
    API --> ORQ[Orquestador Central]

    ORQ --> INV[Agente Investigador]
    ORQ --> RESP[Agente de Respuesta]

    INV --> RAG[Sistema RAG]
    RAG --> DB[(ChromaDB)]

    INV --> LLM[Modelo LLM Ollama]
    RESP --> LLM

    LLM --> SUP[Agente Supervisor]
    SUP --> OUT[Respuesta al Usuario]
