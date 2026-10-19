# Estación 10 NOVA · actualizaciones

Este repositorio público sirve **exclusivamente** para anunciar y distribuir nuevas versiones del POS de Windows. No contiene clientes, ventas, códigos NIP ni respaldos.

## Estado inicial

- Versión inicial conectada: **0.6.1**.
- La aplicación consulta `latest.json` desde **Configuración → Actualizaciones → Buscar actualizaciones**, estando dentro con el perfil de dueño.
- Si `version` coincide con la versión del POS, muestra "Está actualizado".
- La caja, el historial nuevo y los clientes se guardan localmente en la PC; no dependen de este repositorio.

## Publicar una futura modificación

1. Crear desde el código fuente privado de NOVA un `app.asar` nuevo. Debe incluir `package.json` con la versión siguiente (por ejemplo `0.6.2`) y la misma versión en la constante `CURRENT_VERSION` de `main.cjs` y en la pantalla de ajustes.
2. Llamar al archivo `Estacion10-NOVA-0.6.2.asar` (sustituir por la versión correspondiente).
3. Crear una **Release** de GitHub con etiqueta `v0.6.2`, adjuntar ese archivo **.asar** y publicar la Release. Si se agregó el archivo después de publicar, editar la Release para volver a ejecutar el flujo.
4. El flujo `Activar nueva versión en el POS` comprueba el archivo, calcula el SHA-256 y actualiza `latest.json`.
5. En el POS, pulsar **Buscar actualizaciones** y **Actualizar ahora**. El POS verifica el SHA-256, valida la versión del paquete, sustituye `app.asar`, reinicia y conserva el respaldo anterior `app.asar.previous`.

**Importante:** nunca subir aquí datos de clientes, ventas, sellos, contraseñas, configuraciones privadas o el archivo SQLite. Se debe probar cualquier paquete nuevo antes de publicar la Release. No cambiar el nombre del repositorio sin actualizar primero `MANIFEST_URL` en los instaladores existentes.

> Nota: las actualizaciones requieren conexión a internet y el proceso de instalación de Windows puede necesitar permisos sobre la carpeta de la aplicación. El cobro ordinario funciona sin internet.
