# ROADMAP & DECISIONES — HH TRACKER

> Bitácora de decisiones de arquitectura, investigación y funcionalidades futuras. A diferencia de `PROJECT_LOG.md` (qué se construyó), este documento registra **por qué** se decidió algo y **qué falta por evaluar/construir**, para retomarlo sin perder contexto.

---

## 1. Decisiones de arquitectura tomadas

### Base de datos: Supabase (PostgreSQL) en vez de Firebase
- **Contexto**: la propuesta externa de MorgansMedia (ago-2026) usa PostgreSQL, no Firestore. Se evaluó por qué y se decidió migrar.
- **Motivo real**: no es la base de datos en sí — es que la capa financiera (tarifas con vigencia, márgenes, costo empresa protegido por rol) necesita transacciones relacionales y autorización en servidor, algo que Firestore "puro" (como se usaba hasta ahora: blobs JSON leídos directo por el cliente) no puede dar sin reconstruir a mano lo que Postgres + RLS ofrecen de fábrica.
- **Por qué Supabase y no Postgres a pelo**: da auth incluido + Row Level Security (RLS) + Postgres gestionado, en un tier gratuito más que suficiente para <20 usuarios. Evita construir un backend propio desde cero.
- **Estado**: decidido, pendiente de ejecutar (ver sección 3).

### Camino de desarrollo: prototipo local primero, nube después
- Se construye y valida en local (HTML/JS + `localStorage`, sin costo, sin cuentas) antes de invertir en infraestructura. Cuando la empresa apruebe, el mismo código de UI se conecta a Supabase reemplazando solo la capa de persistencia (`persistProjects/persistPeople/persistEntries/persistConfig`).
- **Estado**: ✅ hecho — ver PR #1 (fusionado 2026-09-02). App corriendo 100% local, sin Firebase.

---

## 2. Checklist de seguridad para la migración a Supabase (investigación 2026-09-02)

Investigación sobre errores comunes de seguridad en apps construidas con IA ("vibe coding") — varios calzan exactamente con lo que tenía la versión anterior con Firebase (API keys expuestas, cero autenticación). Checklist a seguir al construir la capa Supabase:

- [ ] **RLS (Row-Level Security) activado en cada tabla desde el día uno** — no dejarlo para después.
- [ ] **Nunca exponer la `service_role key` en el navegador.** Solo `anon key` + JWT del usuario en el cliente; la service key solo se usa server-side para tareas administrativas.
- [ ] Empezar las políticas de RLS simples y agregarlas incrementalmente, probando cada una (políticas muy complejas de entrada son difíciles de depurar).
- [ ] Usar el CLI de Supabase con migraciones versionadas en git, no solo clics en el dashboard web — mismo criterio que ya seguimos con el resto del código.
- [ ] Verificar que ningún endpoint/función confíe solo en el rol mostrado en el cliente — la protección real del "costo empresa" debe evaluarse en servidor (RLS o función), no en JavaScript del navegador (que es lo que hace hoy el selector "Vista como…", que es solo una simulación visual).
- [ ] Considerar JWT con claims custom (tenant/rol embebido en el token) si las políticas RLS con subconsultas resultan lentas — no es necesario a este volumen (<20 usuarios) pero queda anotado.

**Fuentes de la investigación**: ver resumen completo en la conversación del 2026-09-02; búsqueda cubrió Supabase RLS best practices, errores comunes de "vibe coding" (API keys expuestas, RLS desactivado), y comparación de boilerplates SaaS open-source (Next.js + Supabase) — se descartó partir de un boilerplate porque todos traen multi-tenancy/billing que no aplican a un tool interno de un solo tenant.

---

## 3. Backlog de funcionalidades futuras (sin desarrollar aún)

### 3.1 · Gestión comercial: Prospectos y Adjudicación (propuesto 2026-09-02)
**Idea**: agregar una sección de gestión comercial, separada del seguimiento de proyectos activos:
- **Prospectos / Pipeline**: registro de oportunidades comerciales antes de ganarse — cliente, línea de negocio, monto estimado, etapa (ej: Prospección → Propuesta enviada → Negociación → Adjudicado/Perdido), fecha de cada etapa.
- **Adjudicación**: cuando un prospecto se marca "Adjudicado", se registra la fecha y se convierte en Proyecto real (reutilizando los mismos campos que ya existen: monto de venta, cliente, línea de negocio), sin duplicar carga de datos.
- **Separación clara de vistas**: una vista para "lo que estamos vendiendo" (pipeline comercial) y otra para "lo que ya estamos ejecutando" (proyectos activos, que es lo que existe hoy).

**Evaluación de factibilidad**: ✅ factible y de bajo esfuerzo adicional. El modelo de datos actual de `proyectos` (con `status: 'iniciar'|'activo'|'pausa'|'cerrado'`, cliente, línea de negocio, monto de venta) ya es 80% compatible — lo que falta es:
1. Un estado previo a "iniciar" que represente el pipeline comercial (prospecto no ganado aún), con sus propias etapas.
2. Fecha de adjudicación como campo explícito (hoy no existe ningún campo de fecha de venta/adjudicación, solo fecha de inicio/cierre de ejecución).
3. Una vista/tab nueva tipo "Comercial" en el menú principal, separada de "HH" — para no mezclar pipeline de ventas con ejecución de proyectos ya ganados.
4. Métricas propias de esa vista: tasa de conversión (adjudicados / prospectos totales), tiempo promedio de cierre, pipeline valorizado por etapa.

**No incluido en el alcance de la propuesta de MorgansMedia** — ellos solo contemplan "prospección" como las horas planificadas dentro de un proyecto ya creado por el Jefe de Proyecto, no un pipeline comercial pre-venta. Sería un diferenciador de nuestra versión.

**Cuándo abordarlo**: después de validar con la empresa la capa financiera actual (tarifas/costos/márgenes/facturación) y de decidir la migración a Supabase — es una extensión natural del mismo modelo de datos, no un cambio de arquitectura.

### 3.2 · Asistente de IA embebido en el dashboard (propuesto 2026-09-02)
**Idea**: un asistente conversacional dentro de la app que responda preguntas en lenguaje natural sobre los datos reales ("¿qué proyecto tiene peor margen este mes?", "¿quién tiene capacidad disponible en octubre?"), usando el SDK de Claude/Anthropic.
- **Motivación**: surgió al revisar el ecosistema de agentes/skills de Anthropic (`awesome-llm-apps`, `anthropic-sdk-typescript`, `claude-agent-sdk`) — es un diferenciador que la propuesta de MorgansMedia no ofrece (su plataforma es 100% dashboards/tablas, sin lenguaje natural).
- **Cuándo abordarlo**: fase posterior a tener los datos reales en Supabase — un asistente de IA es más valioso una vez que hay datos reales sobre los que preguntar.

### 3.3 · Fases ya contempladas por la propuesta externa (referencia, no compromiso)
Quedan documentadas por si en algún momento se retoman ideas de ahí, aunque no se haya decidido construirlas nosotros:
- Portal de registro de horas para consultores (autoservicio, sin depender de planillas Excel).
- Integración directa con NetSuite (conciliación automática de facturación).

---

## 4. Cómo usar este documento
Antes de retomar el proyecto tras una pausa, leer este archivo junto con `PROJECT_LOG.md`. Al tomar una decisión de arquitectura o al proponer una funcionalidad nueva que no se construye de inmediato, agregarla aquí en la sección correspondiente en vez de dejarla solo en la conversación.
