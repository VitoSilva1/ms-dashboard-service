# ms-dashboard-service

Microservicio orientado a consolidar los datos de ingresos y gastos para alimentar los **widgets del dashboard**. Recibe peticiones del frontend y compone respuestas listas para gráficas (JSON con totales, comparativas y series temporales).

> **Estado actual:** pendiente de implementación. Este README define el alcance y las dependencias esperadas.

## Objetivo
- Consultar `ms-income-service` y `ms-expense-service` para combinar información por usuario.
- Entregar métricas como: balance mensual, top categorías de gasto, distribución de ingresos, etc.
- Exponer endpoints `/dashboard/overview`, `/dashboard/categories`, `/dashboard/incomes-vs-expenses`.

## Diseño propuesto
- FastAPI con tareas asincrónicas (`httpx.AsyncClient`) para llamar a los demás servicios en paralelo.
- Caché corta (Redis) para evitar recalcular métricas con cada solicitud.
- Pruebas unitarias con respuestas mockeadas de los otros microservicios.

Mientras se completa este servicio, el frontend obtiene la información directamente de los servicios de ingresos y gastos.
