# Tablero del equipo: instalación

Son 3 piezas: **Google Sheet** (base de datos), **Apps Script** (backend + emails) y **GitHub Pages** (la página que abre todo el equipo).

---

## 1. Planilla y Apps Script

1. En Google Drive, creá una planilla nueva. Por ejemplo: `Tablero del equipo - BD`.
2. Andá a **Extensiones → Apps Script**.
3. Borrá lo que haya en `Código.gs` y pegá todo el contenido de **Code.gs**. Guardá con Ctrl+S.
4. Arriba, elegí la función **`setup`** y tocá **Ejecutar**. Aceptá los permisos (te va a pedir acceso a Sheets y a Gmail para los emails).
5. Volvé a la planilla: se crearon 4 hojas.
   - **Equipo**: cargá a cada persona con **Nombre, Sector, Email y Activo (SI/NO)**. Los 4 que vienen cargados son ejemplos, así que corregilos o agregá los que falten.
   - **Config**: título, avisos y hora del resumen (ver punto 4).
   - **Estados** y **Bitacora**: se llenan solas, no hace falta tocarlas.
6. Refrescá la planilla. Aparece el menú **Tablero**; desde ahí podés programar el resumen y enviar uno de prueba.

## 2. Publicar el Apps Script como aplicación web

1. En el editor de Apps Script: **Implementar → Nueva implementación**.
2. Tipo: **Aplicación web**.
   - Ejecutar como: **Yo**
   - Quién tiene acceso: **Cualquier usuario**
3. **Implementar** y copiá la URL (termina en `/exec`).

> ⚠️ Cada vez que cambies el código: **Implementar → Gestionar implementaciones → lápiz → Versión: Nueva versión → Implementar**. Si no lo hacés, la URL sigue usando la versión vieja.

## 3. Subir la página a GitHub Pages

1. Abrí **index.html** y en la línea 10 reemplazá `PEGAR_AQUI_LA_URL_DE_APPS_SCRIPT/exec` por la URL que copiaste.
2. En GitHub, creá un repositorio nuevo (por ejemplo `tablero-equipo`) y subí **index.html**.
3. Andá a **Settings → Pages → Source: Deploy from a branch → main / (root) → Save**.
4. En 1 o 2 minutos queda online en `https://TU-USUARIO.github.io/tablero-equipo/`.
5. Pasale ese link al equipo. En la PC lo pueden fijar como pestaña o marcador, y en el celular usar "Agregar a pantalla de inicio".

## 4. Notificaciones por email (hoja Config)

| Clave | Qué hace |
|---|---|
| `RESUMEN_DIARIO` | `SI` = de lunes a viernes llega un email con en qué está cada uno, la bitácora del día y quién no actualizó |
| `HORA_RESUMEN` | Hora del resumen (ej. `17`). Después de cambiarla: menú **Tablero → Programar resumen diario** |
| `EMAILS_RESUMEN` | A quién le llega. Si queda vacío, les llega a todos los que tienen email en la hoja Equipo |
| `AVISO_INMEDIATO` | `SI` = manda un email cada vez que alguien actualiza (viene en `NO` para no llenar la casilla) |
| `EMAILS_AVISO_INMEDIATO` | A quién le llega el aviso inmediato, por ejemplo solo el jefe. Si queda vacío, les llega a todos menos a quien actualizó |
| `HORAS_ALERTA` | Después de cuántas horas sin actualizar la tarjeta se marca en amarillo |
| `TITULO` | Nombre que aparece arriba en la página y en los emails |

**Para activar el resumen:** menú **Tablero → Programar resumen diario** (una sola vez). Para probarlo al instante: **Tablero → Enviar resumen ahora**.

> Gmail gratuito permite unos 100 destinatarios por día con Apps Script. Con el resumen diario sobra. Si activan el aviso inmediato para todos, conviene poner uno o dos destinatarios fijos.

## 5. Cómo lo usa el equipo

- Elegís tu nombre (queda recordado en esa PC), marcás **Presencial** o **Remoto**, escribís "Estoy con…" y apretás **Enter** o **Actualizar**.
- La página se refresca sola cada minuto.
- Si tocás la tarjeta de una persona, la bitácora de abajo muestra solo lo que hizo esa persona hoy.
- Una tarjeta en amarillo significa que esa persona lleva varias horas sin actualizar o todavía no cargó nada hoy.
- El historial completo queda en la hoja **Bitacora** (sirve también como registro para ISO).

**Regla sugerida para el equipo:** actualizar al llegar, cada vez que cambiás de tarea y antes de irte.
