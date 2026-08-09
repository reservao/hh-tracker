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

### [2026-08-09] - Simplificación del Dashboard y Filtro Dinámico Unificado por Estructura
- **Eliminación de Pestañas Redundantes**: Se eliminaron las 4 sub-pestañas desuso de la navegación del Dashboard (`🏢 Jerarquía (Drilldown)`, `📁 Todas las Unidades`, `🏷️ Todas las Líneas`, `📊 Todos los Proyectos`).
- **Perspectivas Activas**:
  - `🌐 Resumen Global`
  - `👥 Todo el Equipo`
- **Nuevo Panel de Filtro por Estructura**:
  - Se agregaron desplegables interactivos integrados en el panel de control: **Unidad de Negocio**, **Línea de Negocio** y **Proyecto**.
  - **Dinámica 100% Reactiva**: Al seleccionar cualquiera de estos tres filtros (o combinarlos), todo el Dashboard (KPIs superiores, gráficos de portafolio, tablas de cumplimiento Nivel 1-3 y Matriz Heatmap) se filtra en tiempo real para mostrar únicamente la información seleccionada.
  - Botón rápido `🧹 Limpiar Filtros` para restaurar la vista completa.
- **Adaptabilidad Responsive**: 100% responsivo para PC, Tablet y Celulares.
- **Modo de Sincronización**: Sincronización manual (`git pull` / `git push`).

---

## 🎯 3. Estado Actual de la Aplicación
- **Archivos Clave**:
  - `index.html`: Dashboard simplificado, reactivo y con arquitectura de filtros dinámicos.
  - `PROJECT_LOG.md`: Bitácora de contexto e historial.
  - `firebase.json` / `.firebaserc`: Despliegue en Firebase Hosting (`hh-circularexpande`).
  - `.github/workflows`: CI/CD para despliegue automático desde GitHub.
- **Estado**: Totalmente funcional, simplificado y optimizado.

---

## 📋 4. Próximos Pasos Pendientes
1. Subir `index.html` y `PROJECT_LOG.md` actualizados a GitHub para aplicar este Dashboard simplificado y dinámico en producción.
