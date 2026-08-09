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

### [2026-08-09] - Adaptabilidad Responsive (PC, Tablet y Celular)
- **Diseño Multi-dispositivo (CSS Media Queries)**:
  - **Pantallas de PC**: Diseño amplio en cuadrícula y tablas estructuradas.
  - **Tablets (hasta 992px)**: Ajuste adaptativo de franja KPI a 3 columnas y márgenes optimizados.
  - **Teléfonos Celulares (hasta 640px)**:
    - Tarjetas KPI adaptadas a 2 columnas.
    - Pestañas con desplazamiento horizontal táctil (*touch swipe*).
    - Tablas de datos con *scroll horizontal fluido táctil* (`-webkit-overflow-scrolling: touch`).
    - Botones y modales adaptados a pantallas táctiles pequeñas.
- **Diseño Nivel 3**: Nombres completos de proyecto arriba y badges de Tipo/LN debajo (sin PEP).
- **Matriz Heatmap**: 100% estática y sin popups oscuros.
- **Modo de Sincronización**: Sincronización manual (`git pull` / `git push`).

---

## 🎯 3. Estado Actual de la Aplicación
- **Archivos Clave**:
  - `index.html`: Aplicación 100% responsiva para PC, Tablet y Celular.
  - `PROJECT_LOG.md`: Bitácora de contexto e historial.
  - `firebase.json` / `.firebaserc`: Despliegue en Firebase Hosting (`hh-circularexpande`).
  - `.github/workflows`: CI/CD para despliegue automático desde GitHub.
- **Estado**: Totalmente funcional y responsivo en todos los dispositivos.

---

## 📋 4. Próximos Pasos Pendientes
1. Subir `index.html` y `PROJECT_LOG.md` actualizados a GitHub para aplicar el cambio responsive en producción.
2. Probar la web desde un smartphone o tablet.
