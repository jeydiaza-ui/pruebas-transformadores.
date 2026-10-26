# Pruebas de Transformadores (PWA)

Aplicación web de una sola página para registrar y documentar pruebas de transformadores en campo:

- **Índice horario y cableado** (grupos Yy, Dy, Yd, Dd; polaridad monofásica).
- **Relación de transformación** (TTR o tensión de red, por fase y por posición de tap).
- **Resistencia de aislamiento** (puntual, DAR, PI, escalonada y rampa; corrección a 20 °C).
- **Resistencia de devanados** (corrección por temperatura, desbalance y comparación con fábrica).
- **Informe** con datos de empresa y cliente, tablas, gráficos, fotos, observaciones, impresión a PDF y exportación JSON.

Versión actual: **4.0.0** (2026-10-26).

- App publicada: <https://jeydiaza-ui.github.io/pruebas-transformadores./>
- Repositorio: <https://github.com/jeydiaza-ui/pruebas-transformadores.>

## Uso

1. Abre la URL en Chrome (Android, Windows) o instálala con **Instalar aplicación** / **Agregar a pantalla de inicio**.
2. Elige el tipo de transformador y las pruebas.
3. Llena las lecturas. Las tensiones se pueden escribir como `13200` o `13.200`; los decimales van con coma (`13,2`).
4. Toca **Informe**, completa los datos y usa **Imprimir / PDF**, **Copiar** o **Guardar informe**.
5. Antes de empezar otro trabajo, toca **Nuevo trabajo** (borra solo lo que está en pantalla).

También funciona sin internet después de la primera visita, y se puede abrir el `index.html` directamente desde el disco (sin instalación PWA).

## Dónde quedan los datos

Todo se guarda **solo en el navegador de ese dispositivo**:

- `localStorage`: datos del trabajo en curso y preferencias.
- `IndexedDB` (`unif_informes`): informes guardados con sus fotos.

No hay servidor, cuenta ni nube. Si se borran los datos del sitio, se cambia de navegador o de dispositivo, los informes desaparecen.

- Usa **Exportar todo** para descargar un respaldo `transformadores_respaldo_AAAA-MM-DD.json`.
- Restaura con **Importar informe o respaldo**.
- La app pide almacenamiento persistente al guardar y muestra el espacio usado; aun así, un respaldo externo es la única protección real.

## Estructura del repositorio

```
index.html                 aplicación completa (4 pruebas embebidas)
manifest.json              manifiesto PWA
service-worker.js          caché y funcionamiento sin internet (v4.0.0)
icon-192.png / icon-512.png            iconos normales
icon-maskable-192.png / -512.png       iconos para Android (zona segura)
README.md
CHANGELOG.md
```

## Publicar una versión nueva

El sitio se publica con **GitHub Pages** desde la rama `main` (raíz del repositorio).

1. Cambia `APP_VERSION` en `index.html` y el texto visible `#ver` / `#repver`.
2. Sube `CACHE_NAME` en `service-worker.js` con la misma versión (por ejemplo `transformadores-pwa-v4.0.1`).
3. Actualiza `CHANGELOG.md`.
4. Haz commit y push a `main`. GitHub Pages publica en 1–2 minutos.
5. Abre la URL, recarga y verifica que el pie muestre la versión nueva.

## Decisiones y límites

- **Criterios de aceptación editables.** Los valores por defecto (resistencia mínima, DAR, PI, tolerancias) son referencias de trabajo; ajústalos al procedimiento de tu empresa y a la norma aplicable antes de usarlos como dictamen.
- **Normas citadas como referencia**, no como certificación: IEC 60076-1, IEEE C57.12.90, IEEE 43 y NETA ATS tabla 100.5. La aplicación no sustituye el criterio de un profesional.
- **Cálculos**: la corrección por temperatura usa 2 por 10 °C en aceite y 1,584 por 10 °C en seco; la resistencia de devanados usa K = 234,5 (cobre) y 225 (aluminio). Verifica estas constantes contra tu norma.
- **Datos de clientes**: la app no cifra el almacenamiento local. En equipos compartidos, cualquiera que abra el navegador puede ver los informes guardados.
- **Fotos**: se comprimen a 1000 px y JPEG 0,72; solo se guardan al tocar **Guardar informe**.

## Licencia y responsabilidad

Uso interno. Sin garantía: verifica los resultados antes de emitir un dictamen.
