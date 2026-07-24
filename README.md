# Curva del Olvido — publicar en GitHub Pages

Esta carpeta contiene los 4 archivos que necesitas subir:

- `index.html`
- `manifest.json`
- `icon-192.png`
- `icon-512.png`
- `sw.js`

## Pasos (desde el móvil o el ordenador, sin usar la terminal)

1. Ve a **github.com** y crea una cuenta si no tienes (gratis).
2. Pulsa el botón **"+"** arriba a la derecha → **"New repository"**.
   - Nombre: por ejemplo `curva-olvido`
   - Marca **"Public"**
   - Pulsa **"Create repository"**
3. En la página del repositorio recién creado, pulsa **"uploading an existing file"** (o el botón "Add file" → "Upload files").
4. Arrastra o selecciona los 5 archivos de esta carpeta (`index.html`, `manifest.json`, `icon-192.png`, `icon-512.png`, `sw.js`) y pulsa **"Commit changes"**.
5. Ve a **Settings** (pestaña del repositorio) → **Pages** (menú lateral izquierdo).
6. En **"Source"** elige **"Deploy from a branch"**, rama **`main`**, carpeta **`/ (root)`**, y pulsa **Save**.
7. Espera 1–2 minutos. GitHub te dará una URL parecida a:
   `https://tu-usuario.github.io/curva-olvido/`

## Instalarla en el móvil

1. Abre esa URL en **Chrome** (Android).
2. Ahora sí debería aparecer el aviso automático **"Instalar aplicación"** o, si no, el menú ⋮ → **"Instalar aplicación"** / **"Añadir a pantalla de inicio"**.
3. Confirma. Quedará como icono en el escritorio y se abrirá a pantalla completa, sin barra de navegador.

## Nota importante sobre tus datos

Los repasos se guardan con `localStorage`, ligado a esta URL exacta. Si más adelante cambias de repositorio o de URL, los datos guardados no se trasladarán solos — tendrás que volver a introducir los temas o exportar/copiar los datos antes de migrar.

---

## Sincronizar el progreso entre todos tus móviles (Firebase, gratis)

Para que el progreso se comparta entre dispositivos necesitas una base de datos gratuita en Firebase. Son unos 5 minutos, una sola vez:

1. Ve a **console.firebase.google.com** e inicia sesión con tu cuenta de Google.
2. **"Add project"** (Agregar proyecto) → ponle un nombre, por ejemplo `curva-olvido` → puedes desactivar Google Analytics → **Create project**.
3. En el menú de la izquierda: **Build → Realtime Database → Create Database**.
   - Elige la ubicación (cualquiera te vale).
   - Selecciona **"Start in test mode"**.
4. Ve a la pestaña **"Rules"** de esa misma sección y sustituye el contenido por:
   ```json
   {
     "rules": {
       "syncs": {
         "$code": {
           ".read": true,
           ".write": true
         }
       }
     }
   }
   ```
   Pulsa **Publish**. Esto limita el acceso a la ruta `/syncs/tu-código`, no a toda la base de datos.
5. En la parte de arriba de la página de Realtime Database verás una URL parecida a:
   `https://curva-olvido-default-rtdb.europe-west1.firebasedatabase.app`
   Cópiala.
6. Abre `index.html` (el de esta misma carpeta) con un editor de texto, busca la línea:
   ```js
   var FIREBASE_DB_URL = "";
   ```
   y pega tu URL entre las comillas. Guarda el archivo.
7. Vuelve a subir el `index.html` actualizado a tu repositorio de GitHub (Add file → Upload files, sustituyendo el anterior) y espera un minuto a que GitHub Pages lo actualice.
8. Abre la app en cada uno de tus móviles → toca el botón **⇅** (arriba a la derecha) → escribe **el mismo código** en todos los dispositivos (por ejemplo `diego-estudio-2026`) → **"Guardar y sincronizar"**.

A partir de ahí, cualquier cambio que hagas en un móvil se sube automáticamente y se descarga en los demás la próxima vez que abras la app (o si la dejas abierta, en segundo plano al recuperar conexión).

**Aviso de privacidad:** con estas reglas, cualquiera que conozca tu código exacto podría leer o escribir esos datos (no hay contraseña real, solo el código). Para una app personal de seguimiento de estudio esto es un riesgo bajo, pero usa un código que no sea obvio y no lo compartas.

