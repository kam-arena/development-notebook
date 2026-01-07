# Microsoft Foundry

## 1. Definición y Propósito

**Microsoft Foundry** (anteriormente Azure AI Studio) es la plataforma unificada (PaaS) para el desarrollo, evaluación y gestión del ciclo de vida de aplicaciones de **IA Generativa**. Su objetivo es superar la fragmentación, ofreciendo un entorno único para ingeniería de prompts, RAG (conexión con datos propios) y seguridad de modelos.

**Cronología clave:**

* **Nov 2023:** Nace como *Azure AI Studio* (Preview).
* **May 2024:** Disponibilidad General (GA).
* **Nov 2024:** Rebranding oficial a **Azure AI Foundry**.
* **Actualidad:** Evolución hacia **Microsoft Foundry** integrando agentes autónomos.

---

## 2. Diferenciación de Servicios

En Azure, Foundry actúa como un **orquestador**, no como un recurso de cómputo aislado. Se diferencia de otros servicios por su nivel de abstracción:

| Servicio | Rol (Analogía) | Uso Principal |
| :--- | :--- | :--- |
| **Microsoft Foundry** | **El Taller** | Desarrollo *End-to-End* (Evaluar, Orquestar, RAG). |
| **Azure OpenAI Service** | **Proveedor de Materia Prima** | Acceso "crudo" a modelos GPT/DALL-E vía API. |
| **Azure Machine Learning** | **Laboratorio Científico** | Entrenamiento de modelos propios (Data Science puro). |
| **Copilot Studio** | **Montaje Rápido (Low-Code)** | Chatbots sencillos sin código (SaaS). |

---

## 3. Modelos: OpenAI vs. Open Source

La ubicación del modelo depende de su proveedor:

* **Modelos OpenAI (GPT-4, DALL-E):** Viven dentro del recurso **Azure OpenAI Service**. Son un jardín cerrado.
* **Modelos Abiertos (Llama, Mistral, Phi):** Se acceden desde el **Model Catalog** de Foundry. Se despliegan como **MaaS (Models as a Service)** mediante APIs Serverless.
  * *Nota:* Para usar Llama 3, usas Foundry para obtener la API Key, pero no estás obligado a usar el resto de herramientas de la plataforma.

---

## 4. Arquitectura Interna

Foundry utiliza una jerarquía para separar administración y desarrollo:

1. **Azure AI Hub ("El Centro"):**
    * Nivel de **Administración**.
    * Gestiona seguridad, redes y conexiones a recursos (OpenAI, Search, Storage).
    * Se configura una vez.
2. **Azure AI Project ("El Proyecto"):**
    * Nivel de **Desarrollo**.
    * Entorno de trabajo aislado hijo del Hub.
    * Aquí residen los prompts, flujos, evaluaciones y archivos de datos específicos.

---

## 5. Portales de Acceso

Existen dos puertas de entrada con propósitos distintos:

* **`portal.azure.com` (Infraestructura):** Para administradores. Creación de recursos, gestión de costes (Billing) y permisos (IAM).
* **`ai.azure.com` (Desarrollo):** Para desarrolladores de IA. Es el entorno de trabajo real (IDE) donde se prueban modelos, se crean agentes y se evalúan resultados.

### 🔗 Para profundizar

* [Conceptos fundamentales: Arquitectura de Foundry](https://learn.microsoft.com/es-es/azure/ai-foundry/concepts/ai-resources)
* [Explorador de Modelos (Catalog)](https://ai.azure.com/explore/models)
* [Documentación técnica completa](https://learn.microsoft.com/es-es/azure/ai-foundry/)
