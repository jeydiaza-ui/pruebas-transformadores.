# Cambios

## v4.0.0 — 2026-10-26

Base: v3 del 12/10/2026 (index.html de 141.295 B).

### Nuevo

- Versión visible en la barra y en el pie del informe (`v4.0.0 · 2026-10-26`).
- **Exportar todo**: respaldo único en JSON con todos los informes guardados.
- **Importar informe o respaldo**: acepta archivos `unif-informe` y `unif-respaldo`.
- Código de empresa/técnico en el consecutivo (`INF-JD-0001`) para separar series entre equipos.
- Aviso y bloqueo al guardar un número ya usado por otro informe: permite asignar el siguiente libre o cancelar.
- Observaciones en **Índice horario** (antes solo existían en las otras tres pruebas).
- Indicador de espacio usado y de almacenamiento persistente.
- Solicitud de almacenamiento persistente (`navigator.storage.persist`).
- Iconos *maskable* propios (192 y 512) y `purpose` separado `any` / `maskable`.
- `beforeprint`: el informe se arma también con Ctrl+P o el menú del navegador.
- Estilo `@page` A4 y márgenes para impresión.

### Corregido

- **Números con separador de miles**: `13.200` ahora se lee como 13.200 V en las tensiones (antes 13,2 V). Los ratios TTR siguen aceptando punto decimal (`103.9231`).
- Validación estricta del JSON importado: formato, claves permitidas, tipos, tamaño máximo y fotos solo `data:image/*`.
- Las imágenes (logo y fotos) se insertan solo si son data URL válidas; se evita inyección de HTML desde un archivo importado.
- Al abrir un informe guardado solo se restauran claves de trabajo permitidas.
- Tarjetas vacías de “Datos del cliente/equipo” ya no aparecen en el informe.
- Texto de normas de aislamiento: se sustituye IEC 60085 por NETA ATS tabla 100.5.
- “Pasmount” → “Pad-mounted”.
- Aviso cuando el DAR mínimo configurado es menor que 1,1.
- Service worker: no intercepta otros dominios, solo responde `index.html` a navegaciones y cachea únicamente respuestas correctas.
- Código muerto en TTR (`allInv`, comparación `< 0.0`).
- Mensajes de guardado con `aria-live`.
- `favicon` para evitar 404.

### Pendiente / fuera de alcance

- Criterios de aceptación por defecto sin cambios (requieren validación del procedimiento de la empresa).
- Sin cifrado ni bloqueo por PIN del almacenamiento local.
- Sin sincronización entre dispositivos (solo exportar/importar).

## v3 — 2026-10-12

- Exportar/importar un informe en JSON.
- Campos de cliente y equipo ampliados.
- Mejoras de impresión (saltos de página) y ajuste del grupo Dy5.
- Guardado de informes en IndexedDB con fotos.

## v2 — 2026-10-10

- Informe consolidado con fotos, logo y guardado local.
- Service worker v2.

## v1 — 2026-10-03

- Versión inicial: índice horario, TTR, aislamiento y devanados.
