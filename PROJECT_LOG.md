# PROJECT LOG & HISTORIAL DE DESARROLLO - HH TRACKER

> **Instrucciones para la IA**: Lee este archivo al iniciar cualquier sesión de trabajo en este proyecto para mantener el contexto completo de las decisiones, estado actual y próximos pasos.

---

## 📌 1. Información General del Proyecto
- **Nombre**: HH Tracker
- **Propósito**: Aplicación web interactiva para seguimiento y gestión de Horas Hombre (HH), proyecciones y asignaciones de contratos/proyectos.
- **Tecnologías**: HTML5, Vanilla CSS, JavaScript (ES6+), Firebase / Hosting static setup.
- **Ubicación Principal**: `Downloads/Proyectos IA/hh-tracker`

---

## 🔄 2. Historial de Sesiones y Cambios

### [2026-08-09] - Mejora Visual: Nombres Completos y Distinción de Tipo/Línea en Matriz Nivel 3
- **Visualización sin Truncamiento**: Se eliminó el límite de ancho (`max-width: 300px` con puntos suspensivos `...`) en la Matriz Nivel 3 (Cumplimiento por Proyecto). Ahora los nombres de proyectos se muestran **completos y legibles**.
- **Jerarquía Visual Clara**:
  - Cada fila muestra en la primera línea la etiqueta de tipo (`📂 Proy` o `⚙️ Admin`) junto al nombre completo del proyecto.
  - Debajo muestra un badge con la **Línea de Negocio** (`🏷️ GAL`, `🏷️ Consultoría`, etc.) y el código **PEP**.
- **Ajustes previos**: Matriz Heatmap 100% de solo lectura y remoción de pestaña redundante en HH.
- **Modo de Sincronización**: Sincronización manual (`git pull` / `git push`).

---

## 🎯 3. Estado Actual de la Aplicación
- **Archivos Clave**:
  - `index.html`: Aplicación con diseño optimizado para legibilidad completa de nombres de proyectos y clasificación.
  - `PROJECT_LOG.md`: Bitácora de contexto e historial.
  - `firebase.json` / `.firebaserc`: Despliegue en Firebase Hosting (`hh-circularexpande`).
  - `.github/workflows`: CI/CD para despliegue automático desde GitHub.
- **Estado**: Totalmente funcional y listo para desarrollo o uso.

---

## 📋 4. Próximos Pasos Pendientes
1. Subir `index.html` y `PROJECT_LOG.md` actualizados a GitHub para aplicar el cambio en producción.
2. Al realizar cambios en el código desde este u otro PC, ejecutar `git push origin main` o subir por la web de GitHub.
