# Revelación AR

Web que, al apuntar la cámara del móvil a un **boceto** (`escaneo.jpg`), revela
encima la **foto real** (`revelacion.jpg`). Usa [MindAR](https://github.com/hiukim/mind-ar-js)
(image tracking en el navegador, sin instalar apps).

## Archivos

| Archivo          | Para qué sirve                                          |
|------------------|---------------------------------------------------------|
| `index.html`     | La experiencia AR (lo que abre el usuario final).       |
| `compilar.html`  | Genera `targets.mind` a partir de `escaneo.jpg`.        |
| `escaneo.jpg`    | El boceto que la cámara reconoce (el marcador).         |
| `revelacion.jpg` | La foto que se superpone al detectar el boceto.         |
| `targets.mind`   | **Lo generas tú** (paso 1). Es el ADN del marcador.     |

## Paso 1 — Generar `targets.mind`

Elige **una** opción:

**Opción A (la más fácil): compilador online**
1. Entra en https://hiukim.github.io/mind-ar-js-doc/tools/compile
2. Sube `escaneo.jpg`.
3. Pulsa *Start* y luego *Download*.
4. Renombra el archivo descargado a `targets.mind` y déjalo en esta carpeta.

**Opción B: con `compilar.html` (local)**
Necesita un servidor local (abrir el HTML con doble clic NO sirve por seguridad
del navegador). Con Node instalado:
```bash
npx serve .
```
Abre `http://localhost:3000/compilar.html`, pulsa el botón y deja el
`targets.mind` descargado en esta carpeta.

## Paso 2 — Probar en el móvil

La cámara **solo funciona en HTTPS** (o en `localhost`). No funciona abriendo el
archivo directamente. Opciones para publicarlo gratis con HTTPS:

- **GitHub Pages**: sube esta carpeta a un repo y activa Pages.
- **Netlify / Vercel**: arrastra la carpeta a netlify.com/drop.

Luego abre la URL en el móvil, pulsa **Empezar**, da permiso de cámara y apunta
al boceto impreso (o mostrado en otra pantalla).

## Consejos para que reconozca bien

- Imprime el boceto en buen tamaño (mínimo ~A5) y con buena luz, sin reflejos.
- Mantén el boceto plano y relativamente quieto al principio.
- Cuanto más detalle/contraste tenga el marcador, mejor lo rastrea.

## Personalizar

- Cambiar la foto revelada → reemplaza `revelacion.jpg` (misma proporción ideal).
- Cambiar el marcador → reemplaza `escaneo.jpg` y **vuelve a hacer el Paso 1**.
- La altura del plano en `index.html` (`height="0.664"`) = alto/ancho del boceto;
  ajústala si cambias de marcador para que la foto encaje exacta.
