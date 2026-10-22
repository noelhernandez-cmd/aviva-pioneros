# Dashboard Pioneros AVIVA · Insumos y gestión comercial

Dashboard interno para seguimiento comercial y operativo de los Pioneros de **Walmart, Sam's Club y Super Bodega Aurrera (SBA)**. Integra metas, ventas, productividad, cobertura de tiendas, Mesa de Riesgos, reconocimientos y análisis ejecutivo.

**Sitio:** https://noelhernandez-cmd.github.io/aviva-pioneros/  
**Repositorio:** https://github.com/noelhernandez-cmd/aviva-pioneros  
**Última actualización de documentación:** 19 de octubre de 2026.

> Herramienta interna de seguimiento. Las proyecciones son estimaciones basadas en los cortes disponibles y no equivalen a ventas de cierre definitivas.

## Módulos actuales

- **Resumen operativo e insumos:** panorama general de tiendas, inventario, cobertura y pendientes.
- **Métricas comerciales:** venta acumulada, objetivos, ritmo, proyección, avance y desglose por vertical/tienda.
- **Seguimiento de productividad:** solicitudes, aprobaciones, desembolsos y objetivos operativos.
- **Mesa de Riesgos:** detección de promotores con proyección inferior al 80%, seguimiento y recuperación.
- **Resultados de recuperación:** comparativos entre proyección inicial y posterior, filtros por semana y fecha de corte, variación en puntos porcentuales y seguimiento por colaborador.
- **Reconocimientos:** mensajes personalizados que se pueden copiar y pegar en Slack.
- **Reporte ejecutivo mensual:** comparativo de casos inicialmente en riesgo frente a su resultado real al cierre, por formato.
- **AVIVA BRAIN / historial:** vistas de seguimiento incluidas en la interfaz.

## Metas: dos conceptos distintos

1. **Meta formal o global asignada:** objetivo oficial fijo. Para octubre de 2026 es **MX$ 4,690,000**. No se modifica automáticamente por vacantes, bajas ni redistribuciones.
2. **Meta general ajustada:** suma de objetivos operativos de tiendas; sí cambia cuando se agregan, retiran o modifican metas por cobertura. Después de retirar Jiutepec, la referencia operativa de octubre es **MX$ 5,460,000**.

Nunca sustituir la meta formal por la ajustada ni mezclar sus porcentajes de avance.

### Corte comercial validado

Al **11 de octubre de 2026, cierre del día**, el desglose validado de **39 tiendas con venta** suma **MX$ 2,349,100**:

| Vertical | Venta acumulada |
| --- | ---: |
| Walmart | MX$ 816,000 |
| Sam's | MX$ 330,100 |
| SBA | MX$ 1,203,000 |
| **Total** | **MX$ 2,349,100** |

El cálculo debe incluir todas las tiendas del desglose, incluida **0412 Periférico Mérida (MX$ 12,000)**. San Martín Texmelucan WM (0365) registra **MX$ 91,600** en este corte.

### Cobertura y vacantes

- **Jiutepec (0407):** Oscar Luna, baja el 12/10/2026; nunca inició operaciones en tienda. Se retira su meta operativa de **MX$ 102,000** de octubre, sin afectar la meta formal asignada. Mantener la tienda como vacante, sin venta ni solicitudes atribuidas.
- **Santín (0443):** Emmanuel, baja el 09/10/2026; seguimiento como vacante.
- Conservar los movimientos e historial comercial previos sin atribuir ventas futuras a personas que ya no están activas.

## Mesa de Riesgos: reglas de negocio

**Umbral:** una proyección de cierre **inferior al 80%** identifica un caso activo en riesgo. Alcanzar **80% o más** implica salir del listado de pendientes; alcanzar **100% o más** merece reconocimiento especial.

### Continuidad semanal

- Al iniciar una semana nueva, arrastrar únicamente a los promotores que **seguían por debajo del 80% al último corte de la semana anterior**.
- Si aún no existe un corte nuevo, mostrar explícitamente que se usa el **último corte disponible**; no presentar esos datos como ventas del nuevo día.
- Los recuperados de la semana anterior permanecen en su historial y reconocimientos, pero no en la lista de pendientes de la semana actual.
- **N.º de caídas:** episodios separados de entrada/reingreso a riesgo, después de haber salido. Permanecer en riesgo dos semanas seguidas **no** significa dos caídas.
- **Semanas consecutivas en riesgo:** número de semanas seguidas por debajo del 80%. Se reinicia tras recuperarse. Es una columna distinta de N.º de caídas.
- Registrar fechas de ingreso, mensaje y salida cuando estén disponibles. Preservar el historial de reincidencias.

**Nota técnica:** el conteo de semanas consecutivas depende de los cortes históricos registrados; se debe validar con semanas futuras y evitar deducir eventos que no existan en los datos.

### Resultados de recuperación

Se muestra la evolución por colaborador, kiosco y formato: proyección inicial, proyección actual, diferencia en **puntos porcentuales (pp)**, N.º de caída, semanas consecutivas y resultado.

El desglose semanal por **Walmart / Sam's / SBA** permite revisar comparados, mejoraron, recuperados del 80 al 99.9%, quienes proyectan 100% o más y quienes retrocedieron.

Distinguir siempre:
- **Mejoró, pero sigue debajo del 80%:** avance positivo; requiere acompañamiento, sin marcarlo como recuperado.
- **Recuperado entre 80% y 99.9%:** salió de riesgo; mensaje de impulso para sostener el ritmo y llegar al 100%.
- **Proyecta 100% o más:** felicitación especial por la recuperación y proyección de cumplimiento o superación.

Los botones **Copiar mensaje** preparan texto personalizado para Slack. **No envían mensajes automáticamente** ni confirman su entrega.

### Cierre mensual e historias de recuperación

Al finalizar el mes, comparar la **primera proyección en riesgo** con el **resultado real de cierre** y presentar por formato:
- Total de personas inicialmente en riesgo, sin duplicar reincidencias.
- Superaron el 100%, mejoraron, quedaron sin cambio o retrocedieron.
- Historias destacadas de quienes comenzaron proyectando un cierre bajo y terminaron cumpliendo o superando la meta.

Antes del último día del mes, el informe definitivo permanece **pendiente de cierre**. Las recuperaciones semanales y proyecciones no deben presentarse como resultados reales finales.

## Datos y persistencia

La aplicación se sirve desde GitHub Pages y contiene lógica del dashboard en `index.html`. Parte del estado de métricas, seguimientos y eventos de riesgo se conserva en **localStorage del navegador**, separado por mes. Esto implica que:

- Los datos guardados localmente pueden variar entre navegadores, equipos o perfiles.
- Publicar cambios en GitHub **no sincroniza automáticamente** esos registros locales.
- Los cortes incorporados directamente en el código y los registros guardados en el navegador deben distinguirse claramente.
- Para un historial auditable compartido, queda pendiente una fuente de datos centralizada y persistente.

## Estado y próximos controles de calidad

- [x] Metas formal y ajustada diferenciadas.
- [x] Corte comercial del 11/oct incorporado y total corregido.
- [x] Jiutepec excluido de la meta operativa.
- [x] Seguimiento de Mesa de Riesgos y filtros semanales.
- [x] Tabla de resultados por formato y mensajes de reconocimiento por nivel.
- [x] Columna de semanas consecutivas separada de caídas.
- [x] Estructura del reporte ejecutivo de cierre mensual.
- [ ] Validar con cortes futuros el arrastre semanal, reincidencias y semanas consecutivas.
- [ ] Verificar consistencia de datos entre dispositivos y considerar persistencia centralizada.
- [ ] Confirmar al cierre del mes los resultados reales e historias de éxito.
- [ ] Validar la visualización pública tras cada despliegue.

## Desarrollo y publicación

La rama `main` alimenta el sitio de GitHub Pages. Los cambios pueden tardar unos minutos en publicarse. Para revisar una actualización, abrir el sitio y, si es necesario, forzar recarga del navegador.

No incluir en el repositorio datos sensibles, credenciales o tokens de Slack.


## Actualización operativa · 19 de octubre de 2026

### Pestaña de Vacantes

El dashboard contempla una vista de vacantes priorizadas por productividad histórica promedio, para orientar cobertura y reclutamiento. **Los datos siguientes son referencias comunicadas para seguimiento; no constituyen un nuevo corte de ventas validado.**

| Tienda | Agosto | Septiembre | Octubre (referencia) | Promedio simple de los 3 meses | Seguimiento |
| --- | ---: | ---: | ---: | ---: | --- |
| Jiutepec | $126,700 | $29,500 | $0 | $52,066.67 | Ingreso a capacitación programado 20/oct |
| Hospital General | $79,800 | $10,000 | $0 | $29,933.33 | Ingreso a tienda programado 21/oct |
| Santín–Vedio | Sin dato | $8,000 | $24,000 | $16,000 (2 meses disponibles) | Vacante, pendiente de confirmar cobertura |
| La Cruz | Sin dato | Sin dato | $0 | No calculable | Vacante; último lugar de prioridad por referencia cero |

**Criterios:** calcular promedios únicamente sobre meses con dato explícito, sin confundir ausencia de dato con ventas cero; ordenar por promedio descendente y mostrar los ingresos *programados* como tales hasta confirmar su realización. La situación de cobertura puede cambiar con nuevas confirmaciones. Los datos anteriores de octubre no deben interpretarse como cierre mensual.

### Rentabilidad por vertical · diseño pendiente de datos financieros

Se propone una sección para **Walmart, Sam's Club y Super Bodega Aurrera** con comparativos de utilidad, margen, porcentaje de tiendas rentables, tiempo al punto de equilibrio, evolución mensual, impacto de vacantes y reconocimiento de mejoras.

- Distinguir **punto de equilibrio mensual** (ingresos del mes ≥ costos del mes) de **recuperación acumulada de inversión** (utilidad acumulada ≥ 0).
- Medir por separado quién llega primero a rentabilidad, quién presenta mayor margen y quién aporta más utilidad absoluta.
- Incorporar una vista ejecutiva por vertical y desglose por tienda, además de simulación con parámetros explícitos.
- **Pendiente:** recibir y validar ingresos, costos, P&L, fechas de inicio y definiciones contables. No publicar utilidades, márgenes ni tiempos como reales hasta disponer de fuentes verificadas.

### Integración con HubSpot · propuesta, no conectada al sitio

Se contempla utilizar HubSpot como fuente de datos comerciales para solicitudes, etapas, montos y fechas, sujeto a los campos y permisos disponibles. **Conectar HubSpot a ChatGPT no sincroniza automáticamente GitHub Pages.** Para actualizaciones automáticas del sitio se requiere una integración independiente y segura (backend o tarea programada), mapeo de identificadores, validación de datos y control de acceso. Nunca publicar tokens, credenciales ni datos personales sensibles en archivos públicos del repositorio.

### Calidad y despliegue

- Conservar una copia o referencia de la última versión estable antes de modificar la interfaz.
- Validar carga inicial, navegación, filtros, pestaña Vacantes y consistencia de totales después de cada despliegue.
- Diferenciar claramente cortes confirmados, datos locales del navegador, proyecciones y ejemplos.
- La actualización de este README **no modifica** el código del dashboard ni confirma que una funcionalidad nueva esté implementada.

## Asignación de metas y movimiento interno · 19 de octubre de 2026

**Metas asignadas (octubre 2026, asignadas por Noel):** 0444 Nicolás Romero Sam's MX$ 70,000 · 0446 Tulancingo Sam's MX$ 100,000 · 0391 Pachuca Sam's MX$ 60,000 · 0264 Plaza El Paseo Walmart MX$ 75,000 · 0365 San Martín Texmelucan Walmart MX$ 125,000 (antes MX$ 310,000).

- **Meta formal:** sin cambio, **MX$ 4,690,000** (Walmart 1,730,000 · SBA 2,350,000 · Sam's 610,000).
- **Meta ajustada (suma de metas por tienda):** **MX$ 5,480,000** (Walmart 2,030,000 · SBA 2,710,000 · Sam's 740,000). Santín (0443) queda sin meta por ser vacante.

**Movimiento interno:** Miguel Vaquero Llanos pasó de 0365 Texmelucan a 0446 Tulancingo Sam's el 12/10/2026. Mijael Gonzalez Espinoza ingresó a 0365 Texmelucan el 12/10/2026.

- Para **seguimiento por persona** (calculadora, Mesa de Riesgos, reconocimientos), Miguel suma los **MX$ 91,600 y 34 solicitudes** de Texmelucan al corte del 11/10, con meta de mes completo. A Mijael se le descuentan esos montos del total de Texmelucan y su meta de MX$ 125,000 corre desde su ingreso.
- Para **totales por formato y cumplimiento formal**, se conserva la venta real de cada tienda: los MX$ 91,600 siguen contando para Walmart.
- La regla está en `OCT_PERSON_ATTRIBUTION_20261019` dentro de `index.html`.

## Corte comercial · 19 de octubre de 2026 (cierre del día)

Venta acumulada por formato: **Walmart MX$ 1,493,989 · SBA MX$ 1,955,300 · Sam's MX$ 700,100 · Total MX$ 4,149,389** (43 tiendas). Se cargó en `METRIC_MONTH_SALES_20261019`; las solicitudes se mantienen al último corte disponible. La fecha de corte de la Mesa de Riesgos y de la calculadora ya no se adelanta a los datos: si hoy es posterior al último corte, se usa el último corte disponible.

**Solicitudes al 19/10 (HubSpot, deals de octubre):** 1,549 en 38 kioscos (Walmart 604 · SBA 737 · Sam's 208), cargadas en `METRIC_MONTH_REQUESTS_20261019`. Los kioscos SBA 0452, 0453, 0454, 0455 y 0456 no aparecen en el reporte de HubSpot; conservan su último dato disponible hasta confirmar su registro.

## Mensajes de Mesa de Riesgos · comparativo diario (20/10/2026)

Los botones **Copiar mensaje** del Plan de recuperación y del Plan de impulso comercial usan el **día en que se envía el mensaje** (no el día del corte) para elegir las recomendaciones, y abren con el comparativo contra el corte anterior: venta y solicitudes sumadas, y si la proyección mejoró, retrocedió o se mantuvo (en puntos porcentuales). El tono se ajusta si la persona está por encima del 100% o del 80%.

Para que el comparativo funcione con cada corte nuevo, agregarlo al final de `METRIC_DAILY_CUTS_202610`.

## Desempeño con historial e incentivos · 20/10/2026

La vista **Desempeño** permite filtrar por formato y nivel (también tocando la tarjeta del nivel) y ordenar por proyección, % real, venta o incentivo estimado. Por promotor muestra agosto y septiembre (venta, % de meta e incentivo final, de los archivos de incentivos) y octubre (venta actual, meta, % real, proyección, nivel e incentivo estimado).

- El historial está en `INCENTIVE_HISTORY_2026` y se asigna **por persona** (correo), aunque haya cambiado de kiosco. Correcciones manuales: 0411 → ana.dominguezr@, 0278 → joan.vazquez@, 0456 → amairani.guzman@. Las filas previas de 0264, 0265 (agosto), 0267, 0276 (agosto), 0365 y 0391 pertenecen a personas anteriores y no se atribuyen al pionero actual.
- El esquema está en `INCENTIVE_SCHEME_2026`. El incentivo de octubre es una **estimación**: venta proyectada × % de bono (categoría y cumplimiento) × multiplicador de la última calidad (B si no hay historial), bloqueado si las solicitudes proyectadas no alcanzan el último candado. Usa la meta asignada completa y no incluye Power Up.

## Power Up HoS · octubre 2026

Tablero dentro de **Desempeño** para el reto de activación: 10 kioscos elegibles (debajo del 80% en septiembre) definidos en `POWERUP_HOS_202610`; no participan 0391, 0264 y 0409 por bajas (los nuevos ingresos no entran). Activación = kioscos con venta ≥80% de su meta de octubre ÷ 10; piso para competir 40% (4 kioscos); premio MX$ 12,500 para un solo HoS. Muestra activados al corte, activación proyectada, lo que falta para el 80% y el ritmo diario necesario. La evaluación oficial es al cierre del mes con datos de la empresa.

## Corte comercial · 20 de octubre de 2026 (cierre del día)

Walmart MX$ 1,587,489 · SBA MX$ 2,062,487 · Sam's MX$ 765,100 · **Total MX$ 4,415,076**. Cargado en `METRIC_MONTH_SALES_20261020` y agregado a `METRIC_DAILY_CUTS_202610` y al historial de impacto semanal. Sin solicitudes nuevas en este corte (se conservan las del 19/10); los mensajes omiten la comparación de solicitudes cuando el corte no las trae.

**Solicitudes al 20/10 (HubSpot):** 1,653 en 38 kioscos (Walmart 650 · SBA 779 · Sam's 224), en `METRIC_MONTH_REQUESTS_20261020`. Los 5 kioscos SBA que no aparecen en HubSpot (0452–0456) conservan su último dato.

## Corte comercial · 21 de octubre de 2026 (cierre del día)

Walmart MX$ 1,659,489 · SBA MX$ 2,145,687 · Sam's MX$ 794,100 · **Total MX$ 4,599,276**. Cargado en `METRIC_MONTH_SALES_20261021` (historial diario e impacto semanal incluidos). Sin solicitudes nuevas en este corte; se conservan las del 20/10.

**Solicitudes al 21/10 (HubSpot):** 2,030 en 43 kioscos, en `METRIC_MONTH_REQUESTS_20261021`. Desde este corte el reporte incluye los kioscos SBA 0452–0456, que antes no venían en las capturas. El comparativo diario de solicitudes solo se muestra cuando el kiosco trae dato en ambos cortes.

## Fichas de Mesa de Riesgos · embudo de solicitudes (22/10/2026)

- Los botones (Descargar ficha PNG, Copiar mensaje, Enviado) quedan **fuera** del recuadro de la ficha, en ambas fichas: la imagen descargada termina en el mensaje de ánimo.
- Bloque nuevo en el Plan de recuperación y el Plan de impulso comercial (`riskFunnelHTML`): **alcance de solicitudes** (real y proyectado vs. la meta mínima de solicitudes de la calculadora), **alcance de venta** (real y proyectado), **venta por solicitud** contra la esperada (ticket × % aprobación × % desembolso del formato) y **solicitudes necesarias para la meta $**, con una lectura del embudo: volumen, conversión, ambos o ninguno. Sin datos de aprobados por kiosco no se distingue entre aprobación y desembolso.

**Tasas reales por formato (octubre, corte 21/10)** en `FORMAT_REAL_RATES_202610`: Walmart 37% aprobación · 72% desembolso · ticket MX$ 8,780; SBA 35% · 74% · MX$ 7,152; Sam's 52% · 72% · MX$ 8,726. La lectura del embudo de las fichas compara cada kiosco contra estas tasas reales; la calculadora conserva sus supuestos.
