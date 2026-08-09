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

### [2026-08-09] - Ajustes de Matriz Heatmap (Visualización Pura y Pestañas)
- **Eliminación de Redundancia de Pestañas**: Se removió la subpestaña Heatmap de la sección **HH**, dejándola únicamente en **Dashboard (Resumen Global)** y en **Dashboard -> Perspectiva "Todo el Equipo"**.
- **Modo 100% Solo Lectura / Visualización**: Se eliminó el enlace de edición de personas (`openPersonModalGlobal`) en los nombres de la tabla Heatmap. La matriz es ahora un componente estrictamente analítico de visualización sin posibilidad de disparar formularios de modificación.
- **Modo de Sincronización**: Sincronización manual (`git pull` / `git push`).

---

## 🎯 3. Estado Actual de la Aplicación
- **Archivos Clave**:
  - `index.html`: Aplicación completa limpia y ajustada para visualización pura del Heatmap.
  - `PROJECT_LOG.md`: Bitácora de contexto e historial.
  - `firebase.json` / `.firebaserc`: Despliegue en Firebase Hosting (`hh-circularexpande`).
  - `.github/workflows`: CI/CD para despliegue automático desde GitHub.
- **Estado**: Totalmente funcional y listo para desarrollo o uso.

---

## 📋 4. Próximos Pasos Pendientes
1. Al realizar cambios en el código desde este u otro PC, ejecutar `git push origin main`.
2. Actualizar este log (`PROJECT_LOG.md`) al finalizar cada sesión de desarrollo relevante.
