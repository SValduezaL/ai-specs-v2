# Especificaciones de IA y Reglas de Desarrollo

Este repositorio contiene un conjunto integral de reglas de desarrollo, estándares y configuraciones de agentes de IA diseñadas para funcionar sin problemas con múltiples copilots de codificación de IA. La configuración es portable y puede importarse a cualquier proyecto para proporcionar desarrollo asistido por IA consistente y de alta calidad.

## 📁 Estructura del Repositorio

```
.
├── ai-specs/                    # Directorio principal con todas las reglas y configuraciones
│   ├── specs/                   # Estándares y especificaciones de desarrollo
│   │   ├── base-standards.mdc   # Reglas centrales de desarrollo (fuente única de verdad)
│   │   ├── backend-standards.mdc
│   │   ├── frontend-standards.mdc
│   │   ├── documentation-standards.mdc
│   │   ├── api-spec.yml         # Especificación OpenAPI
│   │   ├── data-model.md        # Modelos de base de datos y dominio
│   │   ├── development_guide.md
│   │   └── prompts.md           # Plantillas de prompts reutilizables
│   └── changes/                 # Planes de implementación de funcionalidades
│       └── SCRUM-10_backend.md  # Demo: Plan de funcionalidad de actualización de posición
│
├── AGENTS.md                    # Configuración genérica de agente
├── CLAUDE.md                    # Configuración específica de Claude
├── codex.md                     # Configuración de GitHub Copilot/Codex
└── GEMINI.md                    # Configuración específica de Gemini
```

## 🤖 Soporte Multi-Copilot

Este repositorio utiliza **enlaces simbólicos** o **convenciones de nomenclatura** para soportar múltiples copilots de codificación de IA sin duplicación:

- **`AGENTS.md`** → Reglas genéricas de agente (funciona con la mayoría de copilots)
- **`CLAUDE.md`** → Optimizado para Claude/Cursor
- **`codex.md`** → Optimizado para GitHub Copilot/Codex
- **`GEMINI.md`** → Optimizado para Google Gemini

Todos estos archivos referencian las mismas reglas centrales en `ai-specs/specs/base-standards.mdc`, asegurando consistencia entre diferentes herramientas de IA mientras permiten personalizaciones específicas del copilot.

### ¿Por Qué Este Enfoque?

✅ **Fuente Única de Verdad**: Reglas centrales mantenidas en un solo lugar (`base-standards.mdc`)  
✅ **Compatibilidad con Copilots**: Cada herramienta de IA encuentra su configuración usando su convención de nomenclatura preferida  
✅ **Configuración Cero**: Importa a un nuevo proyecto y funciona inmediatamente  
✅ **Actualizaciones Fáciles**: Actualiza las reglas una vez, todos los copilots se benefician  
✅ **Portable**: Copia esta estructura a cualquier proyecto  

## 🚀 Inicio Rápido

### 1. Importar a Tu Proyecto

```bash
# Clona o copia este repositorio en tu proyecto
cp -r LIDR-ai-specs/* your-project/

# El copilot de IA detectará automáticamente el archivo de configuración relevante
```

### 2. Verificar Configuración

Tu copilot de IA cargará automáticamente:
- **Claude/Cursor**: `CLAUDE.md` → `ai-specs/specs/base-standards.mdc`
- **GitHub Copilot**: `codex.md` → `ai-specs/specs/base-standards.mdc`
- **Gemini**: `GEMINI.md` → `ai-specs/specs/base-standards.mdc`

Todas las rutas y reglas están configuradas para funcionar sin problemas sin ajustes manuales.

## 💡 Uso: Flujo de Trabajo Basado en Comandos

La forma más eficiente de trabajar con esta configuración es usando un flujo de trabajo basado en comandos:

### Paso 1: Enriquecer la Historia de Usuario (Opcional)

Si tu historia de usuario carece de detalle o criterios de aceptación, usa el comando **`enrich-us`** para mejorarla:

```
/enrich-us SCRUM-10
```

Este comando analiza la historia de usuario y genera:
- Criterios de aceptación detallados
- Casos extremos y reglas de validación
- Consideraciones técnicas
- Escenarios de prueba

**Nota**: Omite este paso si tu historia de usuario ya tiene suficiente profundidad y requisitos claros.

### Paso 2: Planificar la Funcionalidad

Usa comandos **`plan-ticket`** para generar planes de implementación detallados:

```
plan-backend-ticket SCRUM-10
```

o

```
plan-frontend-ticket SCRUM-15
```

Esto crea un plan de implementación exhaustivo, paso a paso, en `ai-specs/changes/`.

### Paso 3: Implementar la Funcionalidad

Referencia el plan generado y ejecuta:

```
develop-backend @SCRUM-10_backend.md
```

o

```
develop-frontend @SCRUM-15_frontend.md
```

La IA seguirá el plan precisamente, implementando cada paso con TDD, pruebas adecuadas y actualizaciones de documentación.

### Ejemplo: Implementando SCRUM-10 (Funcionalidad de Actualización de Posición)

#### Paso 1: Enriquecer la Historia de Usuario (Opcional)

**Tú dices:**
```
/enrich-us SCRUM-10
```

**La IA mejora** la historia de usuario con criterios de aceptación detallados y consideraciones técnicas (omite si ya está detallada).

#### Paso 2: Generar el Plan

**Tú dices:**
```
/plan-backend-ticket SCRUM-10
```

**La IA genera:**
- Analiza los requisitos del ticket
- Crea `ai-specs/changes/SCRUM-10_backend.md` con:
  - Contexto de arquitectura
  - Instrucciones de implementación paso a paso
  - Especificaciones completas de pruebas (capas de validación, servicio, controlador)
  - Actualizaciones de documentación de API
  - Reglas de validación
  - Estrategias de manejo de errores

#### Paso 3: Implementar Siguiendo el Plan

**Tú dices:**
```
/develop-backend @SCRUM-10_backend.md
```

**La IA ejecuta:**
1. Crea rama de funcionalidad `feature/SCRUM-10-backend`
2. Implementa función de validación con reglas exhaustivas
3. Implementa capa de servicio con lógica de negocio
4. Implementa controlador con manejo HTTP
5. Añade configuración de rutas
6. Escribe cobertura de pruebas de 90%+ en todas las capas
7. Actualiza documentación de API
8. Ejecuta pruebas y verifica implementación
9. Hace commit y push (configurable para esperar hasta confirmación)

### 📝 Demo de Historia de Usuario Enriquecida

Consulta **`ai-specs/changes/SCRUM-10-Position-Update.md`** para un ejemplo completo de cómo se ve una historia de usuario enriquecida. Este documento integral incluye:

- **Historia de Usuario**: Descripción clara con persona, objetivo y beneficio
- **Especificación Técnica**: Detalles completos de implementación técnica
- **Documentación de Endpoint de API**: Formatos de petición/respuesta, códigos de estado y manejo de errores
- **Campos de Base de Datos**: Todos los campos actualizables con reglas de validación
- **Reglas de Validación**: Requisitos de validación del lado del servidor y del cliente
- **Requisitos de Seguridad**: Necesidades de autenticación, autorización y sanitización de entrada
- **Requisitos de Pruebas**: Pruebas unitarias, pruebas de integración y escenarios de pruebas manuales
- **Criterios de Aceptación**: Criterios de aceptación claros y verificables para cada requisito
- **Requisitos No Funcionales**: Estándares de usabilidad, rendimiento, fiabilidad y seguridad
- **Definición de Terminado**: Lista de verificación completa para la finalización de la funcionalidad

Este documento enriquecido transforma una historia de usuario simple en una especificación detallada que proporciona todo el contexto necesario para implementación autónoma por agentes de IA o desarrolladores.

### 📋 Demo de Plan de Implementación

Consulta **`ai-specs/changes/SCRUM-10_backend.md`** para un ejemplo completo de cómo se ve un plan de implementación de funcionalidad. Este plan integral incluye:

- **Contexto de Arquitectura**: Capas, componentes y dependencias
- **Instrucciones Paso a Paso**: Validación → Servicio → Controlador → Rutas → Pruebas → Documentación
- **Ejemplos de Código Completos**: Implementaciones completas para cada capa
- **Especificaciones de Pruebas Exhaustivas**: Requisitos de cobertura de 90%+ con ejemplos de pruebas
- **Manejo de Errores**: Códigos de estado HTTP, mensajes de error y formatos de respuesta
- **Reglas de Negocio**: Requisitos y restricciones de validación
- **Lista de Verificación de Pruebas**: Pruebas unitarias, manuales, de integración y de regresión

Este plan demuestra cuán detallados y accionables son los planes generados, permitiendo implementación autónoma por agentes de IA.

## 📖 Reglas Centrales de Desarrollo

Todo el desarrollo sigue principios definidos en `ai-specs/specs/base-standards.mdc`:

### Principios Clave

1. **Tareas Pequeñas, Una a la Vez**: Pasos de bebé, nunca adelantarse
2. **Desarrollo Guiado por Pruebas (TDD)**: Escribir pruebas que fallan primero
3. **Seguridad de Tipos**: Código completamente tipado (TypeScript)
4. **Nomenclatura Clara**: Variables y funciones descriptivas
5. **Idioma del código**: Todo el código y nombres de archivos, clases, funciones y variables en **inglés**
5. **Idioma de archivos `.mdc` y `.md`, comentarios y comunicación humana**: Todos los comentarios, documentación y mensajes en **español**
6. **Cobertura de Pruebas de 90%+**: Pruebas exhaustivas en todas las capas
7. **Cambios Incrementales**: Modificaciones enfocadas y revisables

### Estándares Específicos

- **Estándares de Backend**: `ai-specs/specs/backend-standards.mdc`
  - Patrones de desarrollo de API
  - Mejores prácticas de base de datos
  - Directrices de seguridad
  - Requisitos de pruebas

- **Estándares de Frontend**: `ai-specs/specs/frontend-standards.mdc`
  - Patrones de componentes React
  - Directrices de UI/UX
  - Gestión de estado
  - Pruebas de componentes

- **Estándares de Documentación**: `ai-specs/specs/documentation-standards.mdc`
  - Estructura de documentación técnica
  - Documentación de API (OpenAPI)
  - Documentación de código
  - Directrices de mantenimiento

## 🎯 Beneficios

### Para Desarrolladores
- ✅ **Calidad de Código Consistente**: La IA sigue los mismos estándares cada vez
- ✅ **Pruebas Exhaustivas**: Cobertura automática de 90%+ en todas las capas
- ✅ **Documentación Completa**: Especificaciones de API actualizadas automáticamente
- ✅ **Incorporación Más Rápida**: Los nuevos miembros del equipo referencian las mismas reglas
- ✅ **Tiempo de Revisión Reducido**: El código sigue patrones establecidos

### Para Equipos
- ✅ **Flexibilidad de Copilot**: Los miembros del equipo pueden usar su herramienta de IA preferida
- ✅ **Preservación del Conocimiento**: Estándares documentados, no en las cabezas de las personas
- ✅ **Consistencia de Calidad**: Mismos estándares independientemente de quién (o qué) escribe el código
- ✅ **Revisiones de Código Más Fáciles**: Expectativas y patrones claros
- ✅ **Prácticas Escalables**: Los estándares escalan con el equipo

### Para Proyectos
- ✅ **Base de Código Mantenible**: Arquitectura limpia y clara separación de preocupaciones
- ✅ **Código Listo para Producción**: TDD, manejo de errores y validación integrados
- ✅ **Documentación Viva**: Especificaciones de API y modelos de datos siempre actuales
- ✅ **Desarrollo de Funcionalidades Más Rápido**: Implementación autónoma de IA a partir de planes
- ✅ **Menor Deuda Técnica**: Mejores prácticas aplicadas desde el día uno

## 🔧 Personalización

### Adaptando a Tu Proyecto

1. **Actualizar `base-standards.mdc`**: Modifica principios centrales para ajustarse a tus necesidades
2. **Añadir Reglas de Dominio**: Incluye reglas de negocio específicas del proyecto
3. **Extender Estándares**: Añade directrices específicas de tecnología (Vue, Angular, etc.)
4. **Crear Plantillas**: Añade plantillas de prompts en `prompts.md`
5. **Vincular Recursos**: Referencia la documentación específica de tu proyecto

### Manteniendo Estándares

- **Fuente Única de Verdad**: Siempre actualiza `base-standards.mdc` primero
- **Control de Versiones**: Rastrea cambios a los estándares como código
- **Revisión del Equipo**: Los cambios a los estándares deben ser revisados como pull requests
- **Documentación**: Mantén los ejemplos actuales con la implementación real

## 📚 Contexto Técnico

### Ejemplos de Referencia (del Proyecto LIDR)

Los siguientes archivos están incluidos como **ejemplos de referencia** del proyecto LIDR. Debes crear tus propias versiones adaptadas a tu proyecto específico:

- **Especificación de API**: `ai-specs/specs/api-spec.yml` (formato OpenAPI 3.0)
  - *Crea tu propia especificación de API documentando los endpoints de tu proyecto*
- **Modelos de Datos**: `ai-specs/specs/data-model.md` (Esquemas de base de datos, modelos de dominio)
  - *Documenta tu estructura de base de datos y entidades de dominio*
- **Guía de Desarrollo**: `ai-specs/specs/development_guide.md` (Configuración, flujos de trabajo)
  - *Escribe instrucciones de configuración específicas para tu stack tecnológico*


## 🤝 Contribuir

Al contribuir a los estándares:

1. Actualiza `base-standards.mdc` (fuente única de verdad)
2. Prueba con múltiples copilots de IA para asegurar compatibilidad
3. Actualiza ejemplos en la carpeta `changes/` si es necesario
4. Documenta los cambios disruptivos claramente
5. ¡Sigue los mismos estándares que estás definiendo!

## 📄 Licencia

Copyright (c) 2025 LIDR.co
Licenciado bajo la Licencia MIT

**English:**

The content of this repository is part of the AI4Devs program by LIDR.co. If you want to learn to code with AI like the pros and get more templates and resources like these, you can find all the information on the official website: https://lidr.co/ia-devs

**Español:**

El contenido de este repositorio es parte del programa AI4Devs de LIDR.co. Si quieres aprender a programar con IA como los pros, y obtener más plantillas y recursos como estos, puedes encontrar toda la información en la página oficial: https://lidr.co/ia-devs

---

**Made with 🤖 by the LIDR community**

For questions, issues, or suggestions, visit [LIDR.co](https://lidr.co/ia-devs)

