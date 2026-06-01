# Mejoras propuestas para el inconsciente de CORPUS

Este documento describe las mejoras planificadas para el sistema de control inconsciente (autónomo) de CORPUS. No todas están implementadas. Es una hoja de ruta.

---

## Áreas de mejora

| Área | Propuesta | Estado | Prioridad |
|------|-----------|--------|------------|
| **Reflejos de navegación** | Detección y recuperación de obstáculos usando umbrales relativos (sin números mágicos). | En análisis | Media |
| **Reposición de objetos** | Rutina para devolver sillas u objetos a su lugar original tras una colisión. | En análisis | Baja |
| **Anticipación de eventos** | Predicción de trayectorias (ej. atrapar un vaso antes de que caiga) usando visión y modelos precalculados. | En análisis (en pañales) | Baja |
| **Sistema experto por tablas** | Reemplazar IA embebida por tablas de decisión (SQLite con índices) generadas por entrenamiento externo. | En análisis | Media-Alta |
| **Entrenamiento externo** | Usar IA cuántica o clásica en servidor potente para generar las tablas. | En análisis | Media |
| **Actualización por firmware** | Reemplazar el archivo `.db` para mejorar comportamientos sin reprogramar. | En análisis | |

---

## Protocolo de seguridad vital (prioridad máxima)

El inconsciente monitoriza continuamente los signos vitales del paciente a través de la conexión neuronal (o de un canal de respaldo). Si detecta una anomalía, **no espera instrucciones del cerebro principal**. Actúa de inmediato.

### Condiciones de activación

- Frecuencia cardíaca fuera del rango seguro (definido en configuración).
- Saturación de oxígeno (SpO₂) por debajo del umbral.
- Temperatura corporal anormal.
- Pérdida de la conexión neuronal por más de `X` segundos (configurable).
- Detección de inmovilidad súbita (acelerómetro del paciente).

### Acciones inmediatas

1. **Detener cualquier movimiento** del avatar (prioridad absoluta).
2. **Cortar la conexión neuronal** (si estaba activa).
3. **Transmitir alerta de emergencia** por todos los canales disponibles (LoRaWAN, satélite, red móvil).
4. **Enviar posición y signos vitales** al servicio de emergencias (o a los contactos predefinidos).
5. **Esperar instrucciones** (o ejecutar rutinas básicas de primeros auxilios, si el avatar tiene capacidad para hacerlo sin riesgo).

### Jerarquía de prioridades

1. Integridad del paciente.
2. Integridad del avatar.
3. Tareas programadas.
4. Solicitudes del cerebro principal.

**El inconsciente no negocia esta jerarquía.**

---

## Integración con ENA (Interfaz Cerebro-Máquina)

Para que estas mejoras funcionen, ENA debe proporcionar:

| Necesidad de CORPUS | Función de ENA |
|---------------------|----------------|
| **Anticipación de eventos** | Detección de potenciales de movimiento (MRCP) antes de que el cerebro ejecute la orden. |
| **Sistema experto por tablas** | Preprocesamiento de la señal EEG (extracción de bandas, detección de intención). ENA envía características, no ondas crudas. |
| **Seguridad vital** | Monitorización de la calidad de la señal y fatiga mental. ENA puede ignorar órdenes si detecta riesgo. |
| **Redundancia** | Modo de operación de "último recurso" si la conexión neuronal se pierde. |

---

## Versión

- **Documento v1.0** — 1 de junio de 2026.
- **Próxima revisión:** Al implementar cualquiera de las mejoras.
