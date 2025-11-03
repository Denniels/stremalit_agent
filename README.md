# 🤖 Sistema Multi-Agente con LangGraph
**Un sistema inteligente de generación automática de aplicaciones usando arquitectura multi-agente**

![Arquitectura del Sistema](docs/arquitectura_nodos.png)

## 🎯 Descripción del Proyecto

Este proyecto implementa un **sistema multi-agente** que genera aplicaciones Python funcionales automáticamente a partir de prompts en lenguaje natural. Utiliza **LangGraph** para orquestar 7 nodos especializados que trabajan en conjunto para crear, validar y desplegar aplicaciones completas.

### �️ Arquitectura Multi-Agente

El sistema está compuesto por **7 nodos especializados** que procesan el contexto secuencialmente:

```
� Entrada → 🤖 Refinar → 💻 Generar → ✅ Validar → 💾 Escribir → 📦 Instalar → 🏁 Salida
```

#### Los 7 Nodos Especializados:

1. **� NodoEntrada**: Recibe y procesa el prompt del usuario
2. **🤖 NodoRefinarPrompt**: Mejora el prompt usando IA (LMStudio/Groq)
3. **💻 NodoGenerarCodigo**: Genera código Python completo con IA
4. **✅ NodoValidarCodigo**: Valida sintaxis y ejecuta en sandbox
5. **💾 NodoEscribir**: Crea archivos en disco con estructura organizada
6. **📦 NodoInstalar**: Detecta e instala dependencias automáticamente
7. **🏁 NodoSalida**: Genera metadatos y finaliza el proceso

### � Capacidades del Sistema

- **Generación automática** de aplicaciones Python funcionales
- **Soporte múltiples frameworks**: Tkinter, Streamlit, Pygame
- **Validación automática** de código con auto-reparación
- **Instalación automática** de dependencias
- **Nombres descriptivos** para aplicaciones generadas
- **Trazabilidad completa** con métricas detalladas
- **Interfaz web** con Streamlit para interacción fácil

## 📁 Estructura del Proyecto

```
stremalit_agent/
├── 📄 README.md                           # Este archivo
├── 📄 requirements.txt                    # Dependencias del proyecto
├── 📄 .env.example                        # Configuración de ejemplo
├── 📄 meta.json                          # Metadatos del proyecto
├── 📄 ARQUITECTURA_MULTIAGENTE.md         # Documentación arquitectura
├── 📄 prompt_imagen_nodos.md              # Especificaciones visuales
├── 📄 ROADMAP_MEJORAS_FUNCIONALIDAD.md    # Roadmap y mejoras
├── 📄 RESUMEN_SESION_02NOV2025.md         # Estado actual del proyecto
│
├── 📂 src/                                # Código fuente principal
│   ├── 📂 agents/                         # Agentes y manager
│   │   ├── __init__.py
│   │   └── manager.py                     # AgentManager principal
│   │
│   ├── 📂 app/                           # Aplicación Streamlit
│   │   ├── __init__.py
│   │   └── streamlit_app.py              # App principal
│   │
│   ├── 📂 langgraph/                     # Sistema Multi-Agente
│   │   ├── __init__.py
│   │   ├── graph.py                      # Definición del grafo
│   │   ├── nodes.py                      # Los 7 nodos especializados
│   │   └── wrappers.py                   # Wrappers para proveedores IA
│   │
│   ├── 📂 tools/                         # Herramientas y clientes
│   │   ├── __init__.py
│   │   ├── detect_providers.py           # Detección automática
│   │   ├── groq_client.py               # Cliente Groq API
│   │   └── provider_clients.py          # Clientes HTTP
│   │
│   ├── 📂 utils/                         # Utilidades
│   │   ├── __init__.py
│   │   ├── auto_reflexion.py            # Sistema auto-reflexión
│   │   ├── code_fixer.py                # Corrección automática
│   │   ├── funcionalidad_validator.py   # Validador funcional
│   │   ├── logger.py                    # Sistema de logging
│   │   ├── memory_system.py             # Sistema de memoria FASE 3
│   │   ├── sandbox_runner.py            # Ejecución segura
│   │   └── token_meter.py               # Medición de tokens
│   │
│   ├── 📂 knowledge/                     # Base de conocimiento
│   │   └── bug_patterns.json            # Patrones de bugs conocidos
│   │
│   ├── 📂 ui/                           # Interfaz de usuario
│   │   ├── __init__.py
│   │   ├── app_page.py                  # Página principal
│   │   ├── banner.py                    # Banner del sistema
│   │   ├── chat.py                      # Chat y progreso
│   │   ├── config_page.py              # Configuración
│   │   └── diagnostics_page.py         # Diagnósticos
│   │
│   ├── 📂 templates/                    # Plantillas de código
│   │   ├── __init__.py
│   │   ├── modular_app/                # Apps modulares
│   │   └── simple_singlefile/          # Apps simples
│   │
│   ├── 📂 workspace/                    # Apps generadas
│   │   ├── snake_game_YYYYMMDD_HHMMSS/ # Ejemplo: Snake generado
│   │   └── tetris_game_YYYYMMDD_HHMMSS/ # Ejemplo: Tetris generado
│   │
│   └── 📂 docs/                        # Documentación técnica
│       ├── cambios_traduccion_nodos.md
│       ├── diagnostic_execution_fix.md
│       └── test_reports...
│
├── 📂 tests/                            # Tests automatizados
│   ├── tests_integration/              # Tests de integración
│   │   └── test_agent_flow.py
│   └── tests_unit/                     # Tests unitarios
│       └── test_nodes.py
│
└── � scripts/                         # Scripts utilitarios
    ├── setup_stremalit_agent.ps1      # Setup automático
    ├── start_app.bat                  # Inicio rápido Windows
    └── cleanup_workspace.ps1         # Limpieza workspace
```

## 🎤 Temario de la Charla Técnica

### **Duración Total: 90 minutos**

#### **🕐 Parte 1: Demostración en Vivo (25 min)**
- **Generación Snake completa desde cero**
  - Prompt: "Crea un juego snake con controles de flechas"
  - Ejecución del pipeline completo
  - Prueba de la aplicación generada
  - Análisis del código generado automáticamente

- **Generación Tetris con controles específicos**
  - Prompt: "Crea Tetris, ESPACIO para rotar, flechas para mover"
  - Demostración del sistema de memoria FASE 3
  - Controles exactos implementados correctamente

#### **🕑 Parte 2: Arquitectura del Sistema (20 min)**
- **Pipeline Multi-Agente explicado**
  - Los 7 nodos especializados en detalle
  - Flujo de contexto entre nodos
  - Orquestación con LangGraph

- **Sistema de Memoria FASE 3**
  - Base de conocimiento de 13+ patrones de bugs
  - Mejora automática de prompts (+700 caracteres)
  - Aprendizaje continuo del sistema

#### **🕒 Parte 3: Tecnologías y Herramientas (15 min)**
- **Stack tecnológico completo**
  - LMStudio + Qwen2.5 (modelo local)
  - Groq API (fallback remoto)
  - Streamlit (interfaz web)
  - LangGraph (orquestación)

- **Auto-reflexión y corrección**
  - Validación automática de código
  - Detección de 13 tipos de errores
  - Regeneración inteligente hasta funcionar

#### **🕓 Parte 4: Casos Avanzados y Métricas (15 min)**
- **Calculadora científica auto-generada**
- **Métricas impresionantes demostradas**
  - 95%+ aplicaciones funcionales
  - 30-90 segundos por app completa
  - +867 caracteres de mejoras automáticas
  - Sistema aprende de errores previos

#### **🕔 Parte 5: Q&A y Código (15 min)**
- **Preguntas técnicas de la audiencia**
- **Acceso al código completo del repositorio**
- **Próximos pasos y mejoras planificadas**
- **Oportunidades de colaboración**

### **🎯 Lo que los Asistentes Aprenderán**

#### **Para Desarrolladores:**
- Implementación real de sistemas multi-agente
- Técnicas de auto-corrección con IA
- Diseño de sistemas de memoria para LLMs
- Orquestación avanzada con LangGraph

#### **Para Arquitectos de Software:**
- Patrones de diseño para IA generativa
- Validación automática de código generado
- Sistemas de retroalimentación inteligente
- Escalabilidad de pipelines de IA

#### **Para Data Scientists:**
- Integración LLMs en aplicaciones reales
- Optimización de prompts con memoria
- Métricas y monitoreo de sistemas generativos
- Manejo de contexto y tokens

### **🚀 Requisitos para Seguir la Charla**

#### **Conocimientos Recomendados:**
- ✅ Python intermedio/avanzado
- ✅ Conceptos de LLMs y prompting
- ✅ Familiaridad con APIs REST
- ✅ Experiencia con sistemas distribuidos (plus)

#### **Setup Técnico (Opcional):**
```bash
# Solo si quieres probar después de la charla
git clone https://github.com/Denniels/stremalit_agent.git
cd stremalit_agent
# Más instrucciones disponibles el día de la charla
```

## 🛠️ Instalación y Configuración

### Pre-requisitos
- Python 3.10+
- Git
- Un proveedor de IA (LMStudio local o Groq API)

### Instalación Rápida
```bash
# Clonar repositorio
git clone https://github.com/Denniels/stremalit_agent.git
cd stremalit_agent

# Configurar entorno virtual
python -m venv .streamlit_agent
.streamlit_agent\Scripts\Activate.ps1  # Windows
source .streamlit_agent/bin/activate   # Linux/Mac

# Instalar dependencias
pip install -r requirements.txt

# Configurar variables de entorno
cp .env.example .env
# Editar .env con tu configuración

# Ejecutar aplicación
streamlit run src/app/streamlit_app.py
```

## � Uso del Sistema

### Interfaz Web
1. Accede a `http://localhost:8501`
2. Ingresa tu prompt en lenguaje natural
3. Selecciona el proveedor de IA (LMStudio/Groq)
4. Observa el progreso en tiempo real
5. Descarga y ejecuta tu aplicación generada

### Ejemplos de Prompts
```
🐍 "Crea un juego snake con controles de flechas y puntuación"
🧩 "Crea Tetris con ESPACIO para rotar y flechas para mover"
🧮 "Crea una calculadora científica con trigonometría"
📊 "Crea un dashboard con gráficos de ventas mensuales"
🎵 "Crea un reproductor de música con playlist"
```

## 📊 Métricas del Sistema

### Rendimiento Demostrado
- **📈 Tasa de éxito**: 95%+ aplicaciones funcionales
- **⚡ Velocidad**: 30-90 segundos por app completa
- **🧠 Mejoras memoria**: +867 caracteres de optimizaciones automáticas
- **🔄 Auto-corrección**: 13 tipos de errores detectados y corregidos
- **🎯 Precisión**: Controles específicos implementados correctamente

### Estadísticas de Desarrollo
- **340+ líneas** de sistema de memoria avanzada
- **13 patrones** de bugs conocidos y soluciones
- **7 nodos especializados** trabajando en conjunto
- **4096+ tokens** de contexto manejados inteligentemente

## 🤝 Contribución y Colaboración

### Después de la Charla
- 📧 **Email** para consultas técnicas específicas
- 🤝 **LinkedIn** para networking profesional
- 🔄 **GitHub** para seguimiento del proyecto

### Oportunidades de Colaboración
- Implementación en empresas
- Extensión a otros lenguajes de programación
- Integración con sistemas empresariales existentes
- Desarrollo de plugins especializados

## 👨‍💻 Contacto

**Daniel Andrés Mardones Sanhueza**
- **GitHub**: [@Denniels](https://github.com/Denniels)
- **LinkedIn**: [Perfil Profesional](https://www.linkedin.com/in/daniel-andres-mardones-sanhueza-27b73777/)
- **Especialidad**: Sistemas multi-agente e IA generativa

---

## 📄 Licencia

Este proyecto está bajo licencia MIT. Ver `LICENSE` para más detalles.

---

<div align="center">

**🎯 ¿Listo para ver IA que se programa a sí misma?**

*¡Nos vemos en la charla!*

</div>