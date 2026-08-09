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

### [2026-08-09] - Simplificación de Diseño Nivel 3, Heatmap de Solo Lectura y Limpieza de Entorno
- **Diseño Ultra Limpio en Nivel 3 (Matriz por Proyecto)**:
  - **Línea 1**: Únicamente el **nombre del proyecto** en negrita (ej: `3981.N.F99 Competencias Laborales EECC Mantenimiento Planta 2026`).
  - **Línea 2 (Justo debajo)**: Insignia de tipo (`📂 Proy` o `⚙️ Admin`) y la Línea de Negocio (`🏷️ GAL`).
  - **Remoción de PEP**: Se eliminó totalmente el texto `(PEP: ...)` de esta tabla para evitar sobrecarga de texto.
- **Matriz Heatmap 100% Estática (Sin Popups / Sin Pantalla Negra)**:
  - Se removieron los eventos de clic y el modo modal emergente oscuro (`modal-overlay`). La matriz es un tablero estático donde la información se consulta pasando el cursor (`tooltip`).
  - Se eliminó la pestaña redundante de Heatmap en la sección HH (se mantiene únicamente en el Dashboard Global y en Todo el Equipo).
- **Desactivación de Popups en Windows**:
  - Se desactivó la tarea programada de 5 minutos (`AntigravityAutoSync`) y el script `AntigravityRealtimeSync.vbs` para evitar cualquier parpadeo de consola en el sistema operativo.
- **Modo de Sincronización**: Control **manual** (el usuario sube los archivos directamente a GitHub o por Git).

---

## 🎯 3. Estado Actual de la Aplicación
- **Archivos Clave**:
  - `index.html`: Aplicación optimizada, limpia y sin popups.
  - `PROJECT_LOG.md`: Bitácora de contexto e historial.
  - `firebase.json` / `.firebaserc`: Despliegue en Firebase Hosting (`hh-circularexpande`).
  - `.github/workflows`: CI/CD para despliegue automático desde GitHub.
- **Estado**: Totalmente funcional y optimizado.

---

## 📋 4. Próximos Pasos Pendientes
1. Subir `index.html` y `PROJECT_LOG.md` a la web de GitHub para publicar el diseño limpio final en producción.
2. Al realizar cambios desde este u otro equipo, actualizar los archivos en GitHub.
