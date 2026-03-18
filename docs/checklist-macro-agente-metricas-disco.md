# Checklist macro: Agente inteligente de métricas para disco (Stockia)

## Objetivo del documento
Definir una guía práctica para construir, validar y escalar un agente de métricas que genere recomendaciones accionables para operación nocturna (caja, barra, administración y compras).

---

## 1) Definir objetivo del agente (foco inicial)
Elegir **1 problema principal** para el MVP:
- Aumentar ventas.
- Reducir merma/fugas.
- Optimizar stock.
- Mejorar carta.
- Mejorar operación por horarios.

Definir también:
- Qué decisiones debe recomendar.
- Cada cuánto recomendar (diario/semanal).
- Qué área ejecuta cada recomendación.

**Entregable:** 1-pager de alcance del agente + metas del primer trimestre.

---

## 2) Ordenar y asegurar la base de datos
Validar captura correcta de:
- Ventas.
- Productos vendidos.
- Horarios.
- Métodos de pago.
- Stock.
- Recetas por trago.
- Movimientos de inventario.
- Anulaciones.
- Consumos por barra.

Higiene de datos:
- Unificar nombres duplicados/inconsistentes.
- Estandarizar categorías y unidades (botella, ml, porción, etc.).
- Definir reglas de calidad mínimas (campos obligatorios, timestamps consistentes).

**Entregable:** checklist de calidad de datos + diccionario de datos operativo.

---

## 3) Diseñar métricas clave (KPI)
Definir KPIs obligatorios:
- Top ventas por producto.
- Productos sin rotación.
- Margen por producto.
- Consumo real vs. teórico.
- Quiebres de stock.
- Ventas por hora.
- Ventas por barra.
- Ventas por staff.
- Ticket promedio.

Frecuencia:
- Diario: operación y alertas.
- Semanal: ajustes de carta/promo/stock.
- Mensual: performance, márgenes y decisiones comerciales.

**Entregable:** catálogo KPI con fórmula, fuente y responsable.

---

## 4) Crear capa analítica
Separar capas:
1. **Data operacional** (transaccional cruda).
2. **Data analítica** (modelada y limpia).
3. **Insights** (señales + recomendaciones).

Implementar:
- Tablas resumidas/vistas para consultas rápidas.
- Trazabilidad de cálculo por métrica.
- Versionado de reglas para auditoría.

**Entregable:** modelo analítico mínimo + vistas de métricas base.

---

## 5) Partir con reglas simples (antes de IA compleja)
Ejemplos de reglas iniciales:
- Si un producto vende muy poco por 3 semanas → marcar “baja rotación”.
- Si hay sobreconsumo → alertar posible merma/fuga/error operativo.
- Si un producto tiene alto margen y baja venta → recomendar destacarlo.
- Si una barra colapsa en franja horaria → recomendar refuerzo.

Validar en terreno:
- ¿Tiene sentido operativo?
- ¿Se puede ejecutar con el equipo actual?

**Entregable:** librería inicial de reglas + criterios de activación.

---

## 6) Diseñar motor de recomendaciones
Madurez sugerida:
1. Reglas fijas.
2. Umbrales dinámicos.
3. Comparación contra periodos previos.
4. Capa IA para explicación/redacción y priorización.

Cada recomendación debe incluir:
- Qué detectó.
- Por qué lo detectó.
- Qué acción sugiere.
- Impacto esperado.
- Nivel de confianza.

**Entregable:** contrato de salida del motor (JSON/UI schema).

---

## 7) Definir salida del agente (UX operativa)
Canales sugeridos:
- Panel de insights.
- Alertas diarias.
- Resumen semanal.
- Recomendaciones accionables con botón de aplicar.

Priorizar legibilidad:
- Estado (normal/alerta/crítico).
- Responsable sugerido (barra/caja/admin/compras).
- Tiempo recomendado de ejecución.

**Entregable:** wireframe funcional de insights + alertas.

---

## 8) Construir MVP acotado
Alcance MVP recomendado:
- Top sellers.
- Productos muertos.
- Alertas de stock.
- Recomendación simple de carta/precio/promoción.

Evitar en MVP:
- Predicción avanzada.
- Automatización total.
- Modelos complejos sin validación operativa.

**Entregable:** MVP en producción controlada con logging de recomendaciones.

---

## 9) Validar en operación real (Berlín / disco piloto)
Proceso:
- Correr durante varias semanas con datos reales.
- Contrastar recomendaciones vs. realidad de turno.
- Incorporar feedback de administración, caja y barra.

**Entregable:** reporte de validación con ajustes de reglas.

---

## 10) Medir impacto del agente
Medir variación en:
- Ventas.
- Quiebres de stock.
- Merma/fuga.
- Rotación de productos.
- Margen.

Atribución:
- Identificar cuáles recomendaciones sí generan mejora.
- Eliminar recomendaciones sin impacto.

**Entregable:** tablero de impacto del agente (antes/después).

---

## 11) Agregar inteligencia avanzada
Cuando el MVP funcione:
- Predicción de demanda.
- Sugerencias de compra.
- Pricing dinámico asistido.
- Análisis por clima/eventos/fecha.
- Recomendaciones por tipo de cliente y horario.
- Alertas de potencial fuga/robo.

**Entregable:** roadmap de capacidades avanzadas por prioridad.

---

## 12) Automatización parcial (con control humano)
Acciones semi-automáticas:
- Cambiar visibilidad de productos.
- Sugerir reposición.
- Proponer ajuste de precio (confirmación manual).
- Activar promos temporales.

Principio:
- “Human-in-the-loop” para acciones sensibles.

**Entregable:** matriz de automatización (automático / sugerido / manual).

---

## 13) Empaquetar como módulo comercial de Stockia
Definir:
- Qué incluye el módulo IA.
- Qué valor entrega al cliente.
- Cómo se vende.
- Qué plan lo incluye.
- Qué métricas de éxito comercial tendrá.

**Entregable:** ficha comercial + pricing + narrativa de valor.

---

## Orden recomendado de ejecución
1. Asegurar data.
2. Definir métricas.
3. Crear reglas simples.
4. Mostrar insights en pantalla.
5. Validar en operación real.
6. Recién después sumar IA generativa y predicción.

---

## En una frase
Primero construyes un sistema que **entienda la operación**; después haces que **recomiende**; y recién al final haces que **piense** de forma más avanzada.
