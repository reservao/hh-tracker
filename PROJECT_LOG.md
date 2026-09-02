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

### [2026-09-02] - Prototipo local sin Firebase + Capa financiera (tarifas, costos, márgenes, facturación)
- **Contexto**: se recibió una propuesta externa (MorgansMedia) para construir una "Plataforma de Gestión de Horas Hombre, Rentabilidad y Facturación". Se decidió primero prototipar en local la capa que falta, extendiendo esta misma app, antes de evaluar una migración a Supabase/PostgreSQL en producción.
- **Persistencia 100% local**: se eliminó la dependencia de Firebase/Firestore (incluía credenciales expuestas en el HTML y acceso público sin autenticación). Los datos ahora se guardan en `localStorage` del navegador mediante `lsSet`/`lsGet`, detrás de la misma interfaz `persistProjects/persistPeople/persistEntries/persistConfig` que ya usaba el resto del código, para que la futura migración a Supabase solo requiera reemplazar esa capa.
- **Tarifas y costos por rol (UF, con vigencia)**: nueva sección en Configuración (`renderFinanceConfigCard`) para definir el valor UF de referencia, tarifas de venta por rol y costo empresa por hora por rol, cada una con fecha de vigencia (un cambio de tarifa no reescribe meses ya calculados).
- **Tarifa efectiva y tres lecturas de margen**: por proyecto se calcula la tarifa efectiva (venta ÷ horas prospectadas), margen devengado, margen proyectado al cierre y margen comercial de cierre (`margenesProject`), siguiendo la misma lógica descrita en la propuesta externa.
- **Facturación por hitos y descalce**: cada proyecto puede tener hitos de facturación (% de venta, fecha, estado) y se calcula el descalce entre % de esfuerzo consumido y % facturado.
- **Simulación de roles y protección de campo**: selector "Vista como…" en la barra superior (Dirección FCh / Gerente de Unidad / Director de Línea / Jefe de Proyecto / Administrador) que oculta el costo empresa (dato sensible bajo Ley 21.719) para los roles sin esa atribución. Es una simulación en el navegador para validar el concepto con la empresa — la protección real a nivel de servidor llegará con la migración a Supabase.
- **Validado con pruebas automatizadas (Playwright)**: flujo completo de configuración de tarifas/costos, creación de proyecto con monto de venta, proyección de horas por rol, cálculo de márgenes, hitos de facturación y persistencia tras recargar la página, sin errores de consola.



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

### [2026-08-09] - Separación Estricta: Resumen Ejecutivo Global vs. Matriz Mensual (Heatmap)
- **`🌐 Resumen Global`**:
  - Queda **100% como resumen ejecutivo macro**:
    1. Consolidado general y gauges.
    2. Suite de 9 gráficos analíticos por línea y unidad.
    3. Matriz resumida por Unidad de Negocio.
    4. Matriz resumida por Línea de Negocio.
    5. **Matriz Ejecutiva por Proyecto** (`Proyecto | Cliente | Tipo | Meses (Trans/Total) | HH Proyectadas | HH Reales | % Cumplimiento`), **sin columnas mensuales `Ene..Dic`**.
- **`👥 Todo el Equipo`**:
  - Contiene de manera exclusiva el desglose mes a mes:
    1. **`🔥 Matriz de Carga y Disponibilidad (% Ocupación Real vs. Capacidad)`** con la grilla mensual transversal `Ene..Dic`.
    2. Bloque de cards individuales por integrante del equipo.

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

