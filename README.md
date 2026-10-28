# Prácticas Rootz (versión con Firebase)

Carpeta lista para subir a GitHub Pages.

- `index.html`: la herramienta completa (un solo archivo). Ya trae la configuración de tu proyecto `practicas-rootz`.
- `firestore.rules`: reglas de seguridad para pegar en Firebase.

## Cómo funcionan los permisos
Cada persona entra con su cuenta de Google. La herramienta mira si su correo figura en la colección `usuarios` de Firestore:

| rol | puede |
|---|---|
| `editor` | ver, registrar/editar/borrar prácticas y **agregar o quitar tareas** |
| `colaborador` | ver, registrar/editar/borrar prácticas |
| `lector` | solo ver |

Si el correo no figura, ve un aviso de "sin acceso" con el botón "Cambiar de cuenta". Para cerrar sesión: link "Cerrar sesión" arriba a la derecha.

## Paso 1. Pegar las reglas (una sola vez)
1. Firebase, **Firestore Database**, pestaña **Reglas**.
2. Borrá todo, pegá el contenido de `firestore.rules` y tocá **Publicar**.

## Paso 2. Crear las personas autorizadas
En Firestore, pestaña **Datos**, **Iniciar colección**:
1. ID de colección: `usuarios`
2. ID del documento: el correo **en minúsculas**, por ejemplo `castelani83@gmail.com`
3. Campo: `rol` (tipo string) con valor `editor`
4. Guardar. Repetí con cada persona:
   - `castelani83@gmail.com`: `editor`
   - `lucialeiva704@gmail.com`: `editor` (o `colaborador`, como prefieras)
   - la tercera persona: se agrega más adelante con el mismo procedimiento ("Agregar documento" dentro de `usuarios`). No hay que tocar el código ni volver a subir nada.

Para cambiar el rol de alguien: editá el campo `rol` de su documento. Para quitarle el acceso: borrá su documento.

## Paso 3. Subir a GitHub Pages
1. Creá un repositorio en GitHub (por ejemplo `practicas-rootz`). Ojo: el sitio de GitHub Pages gratuito es **público**; los datos están protegidos por el login y las reglas.
2. Subí `index.html` (y, si querés, los otros dos archivos) a la raíz del repositorio.
3. **Settings**, **Pages**, en "Branch" elegí `main` y la carpeta `/ (root)`, **Save**.
4. Esperá uno o dos minutos. El enlace queda: `https://TU-USUARIO.github.io/practicas-rootz/`

## Paso 4. Autorizar el dominio en Firebase (obligatorio)
Firebase, **Authentication**, **Settings** (Configuración), **Dominios autorizados**, **Agregar dominio**: `TU-USUARIO.github.io` (solo el dominio, sin `/practicas-rootz`).
Si no lo hacés, el botón "Ingresar con Google" falla.

## Notas
- La `apiKey` de `index.html` es pública por diseño: no da acceso a los datos. Lo que protege la base son las reglas del Paso 1.
- Los datos que cargaste en la versión de claude.ai no se migran; esta versión arranca vacía.
- En iPhone: si el login no abre, probá en Safari (no en el navegador interno de WhatsApp o Instagram).
