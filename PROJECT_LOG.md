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

### [2026-08-09] - Transformación Visual 2.0 (Rediseño de Píldoras Métricas & Sistema Circular HR)
- **Transformación de Celdas Numéricas (Píldoras de Métricas Visuales)**:
  - Se reemplazaron los números de porcentaje planos por **Píldoras de Métricas Estilizadas (`.pct-pill`)**:
    - 🟢 **Verde Menta (`pct-opt`)**: Cumplimiento óptimo (70% - 110%).
    - 🔴 **Rojo Coral (`pct-over`)**: Sobreejecución (> 110%).
    - 🟡 **Ámbar Dorado (`pct-under`)**: Subejecución (< 70%).
    - ⚡ **Ámbar Alerta (`pct-warn`)**: Horas ejecutadas sin proyección previa.
- **Efectos Interactivos en Filas (`.table-hover-row`)**:
  - Al pasar el cursor sobre cualquier proyecto o unidad, la fila completa resalta con un fondo suave y una **línea de acento azul Circular HR** en el extremo izquierdo (`border-left: 3px solid #0073A8`).
- **Paleta Corporativa Circular HR / Fundación Chile**:
  - Azul Primario `#0073A8`, Azul Noche `#005075` y Turquesa Cyan `#4AEAED`.
- **TopBar con Distintivo Oficial**:
  - `CIRCULAR HR | Fundación Chile` en la cabecera.

### [2026-08-09] - Reorganización del Dashboard: Matriz Heatmap a "Todo el Equipo"
- **Redistribución de Componentes**:
  - **`🌐 Resumen Global`**: Se removió el Heatmap de personas para mantener la pestaña 100% enfocada en métricas macro del portafolio (Consolidado, 9 Gráficos, Matriz por Unidad, Matriz por Línea y Matriz de Cumplimiento por Proyecto).
  - **`👥 Todo el Equipo`**: Se ubicó en la parte superior la **`🔥 Matriz de Carga y Disponibilidad (% Ocupación Real vs. Capacidad)`** por integrante, seguida del bloque de Cards Individuales del Equipo.

---

## 🎯 3. Estado Actual de la Aplicación
- **Archivos Clave**:
  - `index.html`: Aplicación con suite analítica completa (9 gráficos + 3 matrices de cumplimiento).
  - `PROJECT_LOG.md`: Historial de cambios.
  - `firebase.json` / `.firebaserc`: Hosting en Firebase (`hh-circularexpande`).
- **Estado**: 100% Funcional, completo y renovado visualmente.

---

## 📋 4. Próximos Pasos Pendientes
1. Revisión visual por parte del usuario.

