# Rutina

App de entrenamiento personal: 2 días de sala (A y B) más seguimiento de cardio.
Funciona sin internet — los GIFs de cada ejercicio están dentro del HTML.

## Qué hace

- 13 ejercicios con animación e instrucciones paso a paso en español
- Marcás cada serie tocando las barras; al marcar arranca solo el timer de descanso
- Guarda el peso que usaste en cada ejercicio y te lo muestra la próxima vez
- Registro de sesiones de cardio con gráfico de los últimos 14 días
- Todo se guarda en el celular (localStorage). No hay servidor ni cuenta.

## Deploy en Netlify

Es un sitio estático, no hay build.

1. Subí esta carpeta a un repo nuevo en GitHub
2. En Netlify: **Add new site → Import an existing project**
3. Elegí el repo
4. Build command: vacío. Publish directory: `.`
5. Deploy

El `netlify.toml` ya deja configurado el publish directory y los headers del service worker.

## Instalar en el celular

Con el sitio abierto en Chrome (Android):

1. Menú de tres puntos
2. **Instalar aplicación** o **Agregar a pantalla de inicio**
3. Queda como app con ícono propio, sin barra del navegador

En iPhone es desde Safari → Compartir → Agregar a pantalla de inicio.

## Actualizar el contenido

Todo el plan está en el objeto `PLAN` dentro de `index.html`. Cada ejercicio tiene:

```
id      identificador interno
name    nombre que se ve
sets    cantidad de series
reps    texto de repeticiones
cue     la indicación principal (acepta HTML)
key     true = muestra la etiqueta "No lo saltees"
swap    nota aclaratoria opcional
gif     animación en base64
steps   array de pasos en español
```

Después de cambiar cualquier archivo, subí el número de versión en `sw.js`
(`const CACHE = 'rutina-v1'` → `v2`) para que el celular baje la versión nueva.

## Créditos

Animaciones e instrucciones: [exercises-dataset](https://github.com/hasaneyldrm/exercises-dataset)
(MIT). Media © [Gym visual](https://gymvisual.com/), redistribuida con permiso a 180×180.
Para uso comercial hay que sacar licencia propia con Gym visual.
