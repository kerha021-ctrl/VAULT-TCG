# 🃏 VAULT TCG

Juego de cartas coleccionables en 3D para el navegador, inspirado en *Pokémon TCG Pocket*: abre sobres, colecciona, mejora y combate con **tus propias cartas** (imágenes, GIF y video). Todo en **un solo archivo** (`index.html`), sin servidores ni dependencias: funciona en el móvil y en el ordenador.

<p align="center">
  <img src="docs/tienda.png" width="22%" alt="Tienda de sobres">
  <img src="docs/coleccion.png" width="22%" alt="Colección por rareza">
  <img src="docs/ruleta.png" width="22%" alt="Ruleta 3D con mascota">
  <img src="docs/tragaperras.png" width="22%" alt="Tragaperras">
</p>

> Las capturas usan cartas de muestra. Tú pones las tuyas.

---

## ✨ Qué incluye

**Para el jugador**
- 🛍️ **Tienda de sobres** en estantes horizontales por tipo, con precio, cuenta atrás para sobres exclusivos y apertura al estilo Pokémon TCG Pocket (rasgar el sobre, cartas que salen una a una, brillo según la rareza).
- 🌟 **Rangos**: Normal, Rara, Oro, Plata, Diamante, Leyenda, Estrella, **Legendaria** y **Superleyenda**. Las dos últimas tienen animación especial con video de 5 segundos (se puede saltar).
- 🗂️ **Colección** separada por rareza, con orden manual (mantén pulsada una carta y arrástrala), etiquetas y filtros.
- 🔄 **Cartas 3D**: gíralas 360°, voltéalas, ponles contorno y aura que parpadea, descripción, portada trasera, GIF o video (mantén pulsado 2 segundos o toca ▶).
- ⚡ **Mejorar cartas**: une copias iguales para subir un atributo; con dos cartas al máximo se crea una **legendaria** (hasta 400).
- ⚔️ **Batallas** carta contra carta (al mejor de 2 o 3), con tu equipo de 5 cartas, mazos por etiqueta y un rival que puede ser débil, equilibrado o fuerte. Animación 3D: la carta ganadora destruye a la otra.
- 🎰 **Azar**: ruleta 3D y tragaperras con palanca, con una **mascota 3D** que se alegra o se entristece y una nube de cómic con las probabilidades. Solo usa **monedas del juego**.
- 🔊 **Audio**: música del juego, sonidos de batalla (pelea, golpe, victoria, derrota) y un audio por carta. Control de volumen tocando el altavoz.

**Para el administrador** (inicia sesión tocando el logo **VAULT**)
- Crear y editar cartas: nombre, atributos (1–200), rango, colores, fuente, contorno, aura, descripción, GIF/video/portada trasera, audio.
- Crear sobres: precio, tipo/estante, portada, tiempo en tienda (se repite cada 2 semanas) y reordenarlos arrastrándolos.
- Configurar la ruleta y la tragaperras: qué sobres/cartas salen, sus probabilidades, costos y fondo de la sección.
- Subir música y sonidos.
- **Descargar el juego con tus cambios** para compartirlo.

---

## 🚀 Probarlo en local

1. Descarga `index.html`.
2. Ábrelo con doble clic en tu navegador (Chrome, Edge, Firefox o Safari recientes).

> Para iniciar sesión como administrador el navegador necesita un contexto seguro: funciona en `https://`, en `localhost` y al abrir el archivo directamente.

**Acceso de administrador por defecto:** usuario `admin` · contraseña `admin`.
⚠️ **Cámbialos antes de publicar** (ver más abajo).

---

## 🌐 Publicarlo gratis con GitHub Pages

### Opción A · Desde la web de GitHub (sin instalar nada)

1. Entra en <https://github.com> e inicia sesión (o crea una cuenta gratuita).
2. Pulsa **New repository** (el botón verde o el `+` de arriba a la derecha).
3. Ponle un nombre, por ejemplo `vault-tcg`, márcalo como **Public** y pulsa **Create repository**.
4. En la página del repositorio elige **uploading an existing file**.
5. Arrastra `index.html`, `README.md` y la carpeta `docs` (o descomprime el `.zip` y arrastra su contenido) y pulsa **Commit changes**.
6. Ve a **Settings → Pages**.
7. En **Build and deployment**, en *Source* elige **Deploy from a branch**; en *Branch* elige `main` y la carpeta `/ (root)`; pulsa **Save**.
8. Espera de 1 a 5 minutos. La dirección pública aparecerá arriba en esa misma página:

   ```
   https://TU-USUARIO.github.io/vault-tcg/
   ```

### Opción B · Con git (terminal)

```bash
git init
git add index.html README.md docs
git commit -m "VAULT TCG"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/vault-tcg.git
git push -u origin main
```

Luego activa **Settings → Pages** como en los pasos 6 y 7 de arriba.

### Para actualizar la app

Sube de nuevo el archivo `index.html` (reemplaza el anterior) y haz *Commit*. En uno o dos minutos la web se actualiza. Si no ves los cambios, recarga sin caché (`Ctrl + Shift + R`).

---

## 📦 Publicar tu catálogo (cartas, sobres, sonidos…)

El juego guarda los datos **en el navegador de cada persona**, así que tu catálogo no se comparte solo. Para que todos vean tus cartas y sobres:

1. Abre tu copia, inicia sesión como administrador y crea todo lo que quieras.
2. En la pestaña **Crear** pulsa **⬇ Descargar juego con mis cambios**. Se descarga un archivo `vault-tcg.html` con tu catálogo dentro.
3. Cámbiale el nombre a `index.html` y súbelo al repositorio reemplazando el anterior.

Cada jugador empieza con 🪙1000 y su propio progreso; si más adelante subes una versión nueva, recibe tus cambios **sin perder sus cartas**.

**Límites de tamaño:** por la web de GitHub el máximo es **25 MB por archivo**; con git, 100 MB. Comprime las imágenes y evita videos muy pesados.

---

## 🔐 Cambiar usuario y contraseña

La contraseña no se guarda en texto: se guarda su huella SHA-256 al principio del `<script>` de `index.html`.

1. Abre la app en el navegador y pulsa **F12** → pestaña **Consola**.
2. Pega esto cambiando `miusuario` y `micontraseña`, y pulsa Enter:

   ```js
   (async()=>{const u='miusuario',p='micontraseña';const b=await crypto.subtle.digest('SHA-256',new TextEncoder().encode('vault|'+u+'|'+p));console.log([...new Uint8Array(b)].map(x=>x.toString(16).padStart(2,'0')).join(''))})()
   ```
3. Copia el resultado y edita estas dos líneas en `index.html`:

   ```js
   const ADMIN_USER='miusuario',ADMIN_HASH='PEGA-AQUI-LA-HUELLA';
   ```

> ℹ️ Esto es solo una barrera visual: el juego funciona 100 % en el navegador, así que cualquiera que sepa de programación podría saltársela **en su propia copia**. No afecta a los datos de los demás jugadores, que viven en sus dispositivos.

---

## ⚠️ Contenido y derechos

- Sube solo imágenes, videos y audios **de los que tengas derechos** o permiso de uso.
- GitHub **prohíbe contenido sexualmente explícito u obsceno** en sus servicios. No lo incluyas en el repositorio ni en el catálogo que publiques allí. Si quieres compartir un catálogo con ese tipo de material, hazlo por otros medios privados (el archivo descargable funciona en cualquier sitio).
- Las secciones de azar usan **monedas ficticias** del juego; no hay dinero real ni premios reales.

---

## 🛠️ Detalles técnicos

- Un único `index.html` (HTML + CSS + JavaScript, sin librerías). Solo carga *Google Fonts* para los tipos de letra de las cartas; si no hay internet, usa tipos de letra del sistema.
- **Datos**: `localStorage` (cartas, sobres, ajustes, imágenes comprimidas) e `IndexedDB` (videos y audios).
- **Límite de almacenamiento** de `localStorage`: unos 5 MB por navegador. La app avisa si se llena.
- En `github.io`, el almacenamiento se comparte entre todas las páginas de tu usuario (mismo dominio). Borrar los datos del navegador borra el progreso.
- Formatos de video/audio: los que soporte el navegador (MP4/H.264, WebM, MP3, WAV, OGG, M4A…).

---

## 📄 Licencia

Añade la que prefieras desde GitHub: **Add file → Create new file → `LICENSE`** y pulsa *Choose a license template* (por ejemplo MIT).
