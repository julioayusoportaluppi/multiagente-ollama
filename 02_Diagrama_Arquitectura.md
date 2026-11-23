# 02 — Diagrama de Arquitectura

## Arquitectura general

```mermaid
flowchart TD
    U[Usuario] --> UI[Interfaz de usuario / API]
    UI --> O[Orquestador de agentes]

    O --> A1[Agente 1]
    O --> A2[Agente 2]
    O --> AN[Agente N]

    A1 --> T[Herramientas]
    A2 --> T
    AN --> T

    A1 --> M[Memoria]
    A2 --> M
    AN --> M

    T --> OL[Ollama]
    M --> OL

    A1 --> OL
    A2 --> OL
    AN --> OL

    OL --> R[Respuesta generada]
    R --> UI
```

## Flujo de interacción

```mermaid
sequenceDiagram
    actor Usuario
    participant Interfaz
    participant Orquestador
    participant Agente
    participant Herramientas
    participant Ollama

    Usuario->>Interfaz: Envía una solicitud
    Interfaz->>Orquestador: Clasifica y prepara la tarea
    Orquestador->>Agente: Selecciona y delega
    Agente->>Herramientas: Solicita datos o acciones
    Herramientas-->>Agente: Devuelve resultados
    Agente->>Ollama: Genera una respuesta
    Ollama-->>Agente: Retorna el resultado
    Agente-->>Orquestador: Devuelve la solución
    Orquestador-->>Interfaz: Integra la respuesta
    Interfaz-->>Usuario: Presenta el resultado
```

## Responsabilidades por capa

| Capa | Responsabilidad |
|---|---|
| Interfaz | Recibir solicitudes y mostrar respuestas. |
| Orquestador | Clasificar tareas y coordinar agentes. |
| Agentes | Ejecutar tareas específicas con instrucciones y contexto. |
| Herramientas | Acceder a servicios, archivos o acciones externas. |
| Memoria | Conservar el contexto relevante de la interacción. |
| Ollama | Ejecutar localmente los modelos de lenguaje. |
