# 🚀 Proyecto: Prompt generator with 3 outputs for multi AI providers  
### Inteligencia Artificial 

---

## 🧠 Descripción del Proyecto
Este proyecto fue desarrollado durante el **[Hackathon Kavak x OpenAI]**, con el objetivo de integrar las capacidades act para optimizar procesos, mejorar la experiencia del usuario y aplicar **IA generativa** en el análisis de datos en variedad de agentes provedores de IA.

## Ingeniería de Prompts:

• Genera prompts mejorados

## El sistema permite:
- Procesamiento de instrucciones para optimización de la busqueda en un prompt con cada interación.  
- Generación de interacciones de busqueda donde cada interacción mejora la métrica anterior.  
- El sistema que se muestra ayuda a indentificar y corregir problemas comunes, lo que resulta en indicaciones más fiables y efectivas .  
  
---

## 💡 Problema que Resuelve
Se muestran las mejores prácticas para usar conjuntamente agentes SDK para crear una versión de sistemas de optimización del prompt para OpenAI, Gemini y Anthropic.
El proceso de optimización utiliza un enfoque multiagente con agentes de IA especializados que colaboran para analizar y reescribir las indicaciones.

---

## 🧩 Solución Propuesta
Descripción general del sistema
El sistema de optimización de solicitudes utiliza un enfoque colaborativo multiagente para analizar y mejorar las solicitudes. Cada agente se especializa en detectar o reescribir un tipo específico de problema:

**Dev-Contradiction-Checker:** Analiza la solicitud en busca de contradicciones lógicas o instrucciones imposibles, como "usar solo números positivos" e "incluir ejemplos negativos" en la misma solicitud.

**Format-Checker:** Identifica cuándo una solicitud espera una salida estructurada (como JSON, CSV o Markdown) pero no especifica claramente los requisitos de formato. Este agente garantiza que todos los campos, tipos de datos y reglas de formato necesarios estén definidos explícitamente.

**Few-Shot-Consistency-Checker:** Examina conversaciones de ejemplo para garantizar que las respuestas del asistente cumplan con las reglas especificadas en la solicitud. Esto detecta discrepancias entre lo que requiere la solicitud y lo que demuestran los ejemplos.

**Dev-Rewriter:** Tras identificar los problemas, este agente reescribe la solicitud para resolver contradicciones y aclarar las especificaciones de formato, conservando la intención original.

**Reescritura de pocas instancias:** Actualiza las respuestas de ejemplo inconsistentes para que se ajusten a las reglas de la solicitud, garantizando así que todos los ejemplos cumplan correctamente con la nueva solicitud del desarrollador.

Al trabajar juntos, estos agentes pueden identificar y corregir sistemáticamente los problemas en las solicitudes..

---

## 🛠️ Stack Tecnológico
| Categoría | Tecnologías |
|------------|--------------|
| **Frontend** | React, TailwindCSS, Next.js |
| **Backend** | FastAPI, Node.js |
| **IA / ML** | OpenAI API, LangChain, Scikit-learn |
| **Base de Datos** | PostgreSQL |
| **Infraestructura** | Docker, Railway, GitHub Actions |
| **Diseño y Branding** | Figma, Illustrator, Canva |

---

## ⚙️ Instalación y Ejecución

### 1️⃣ Clonar el repositorio
```bash
git clone https://github.com/tuusuario/kavak-openai-hackathon.git
cd kavak-openai-hackathon
```
