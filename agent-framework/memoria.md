# Tipos de memoria en Microsoft Agent Framework

Guía sobre las opciones de memoria disponibles para agentes en Microsoft Semantic Kernel y Agent Framework.

> ⚠️ **Nota:** La funcionalidad de memoria para agentes es experimental y está sujeta a cambios.

## Memoria a Corto Plazo (Historial de Conversación)

El historial de conversación (`ChatHistory`) mantiene el registro de mensajes de una sesión. Es esencial para preservar el contexto y la continuidad.

### Opciones de almacenamiento

1. **Almacenamiento en Memoria** (In-Memory Storage)
   - Por defecto, el historial se guarda en el objeto `AgentThread`.
   - Ideal para desarrollo y pruebas.
   - Se pierde al finalizar la sesión.

2. **Almacenamiento en el Servicio** (In-Service Storage)
   - Algunos servicios (como Azure AI Agent) almacenan el historial en el backend.
   - Se accede mediante un `thread_id`.
   - Requiere un `AgentThread` específico del servicio (ej: `AzureAIAgentThread`).

3. **Almacenamiento Personalizado** (3rd Party Storage)
   - Implementar `ChatMessageStore` para persistir en bases de datos externas.
   - Opciones comunes: Redis, Cosmos DB, Vector Stores.
   - Permite serializar/deserializar el estado para reanudar conversaciones.

### Reducción del historial

Estrategias para gestionar historiales extensos:

| Estrategia | Descripción |
| :--- | :--- |
| **Truncación** | Elimina los mensajes más antiguos al superar un límite. |
| **Resumen** | Condensa mensajes antiguos en un resumen. |
| **Basada en Tokens** | Elimina mensajes cuando se excede el límite de tokens del modelo. |

## Memoria de Pizarra (Whiteboard Memory)

Captura información clave de la conversación (requisitos, decisiones, acciones) incluso cuando el historial se trunca.

### Características

- Extrae automáticamente información relevante de cada mensaje.
- Proporciona contexto adicional al agente en cada invocación.
- Útil para mantener el contexto cuando se aplica truncación.

### Configuración

```python
from agent_framework.memory import WhiteboardProvider

whiteboard_provider = WhiteboardProvider(chat_client)
agent_thread.ai_context_providers.append(whiteboard_provider)
```

### Opciones disponibles

- `MaxWhiteboardMessages`: Número máximo de mensajes a retener.
- `ContextPrompt`: Personaliza el prompt que contextualiza los recuerdos.
- `MaintenancePromptTemplate`: Personaliza cómo se añaden/actualizan/eliminan mensajes.

## Memoria a Largo Plazo (Mem0)

[Mem0](https://mem0.ai) permite recordar preferencias del usuario entre múltiples conversaciones.

### Beneficios

- Aprende de las interacciones con el usuario.
- Almacena memorias asociadas a un `UserId` específico.
- Puede combinarse con Whiteboard para memoria híbrida.

### Uso básico

```python
from agent_framework.memory import Mem0Provider

mem0_provider = Mem0Provider(
    http_client=http_client,
    user_id="U1",
    # Opcional: application_id, agent_id, thread_id
)
agent_thread.ai_context_providers.append(mem0_provider)
```

### Opciones de alcance (Scoping)

| Opción | Uso |
| :--- | :--- |
| `UserId` | Memorias específicas del usuario (largo plazo). |
| `ThreadId` | Memorias de una conversación específica. |
| `AgentId` | Memorias asociadas a un agente particular. |
| `ApplicationId` | Memorias a nivel de aplicación. |

## Combinando Mem0 y Whiteboard

Es posible usar ambos proveedores para lograr un balance entre memoria a corto y largo plazo:

```python
agent_thread.ai_context_providers.append(mem0_provider)       # Largo plazo
agent_thread.ai_context_providers.append(whiteboard_provider) # Corto plazo
```

## 🔗 Para profundizar

- [Documentación oficial: Agent Memory](https://learn.microsoft.com/en-us/semantic-kernel/frameworks/agent/agent-memory)
- [Tutorial: Storing Chat History in 3rd Party Storage](https://learn.microsoft.com/en-us/agent-framework/tutorials/agents/third-party-chat-history-storage)
- [Chat History en Semantic Kernel](https://learn.microsoft.com/en-us/semantic-kernel/concepts/ai-services/chat-completion/chat-history)
