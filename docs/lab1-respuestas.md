# Laboratorio 1 - Preguntas de comprobación

Name: Daniel Campoy

## 1. ¿Cuál es la diferencia entre Working Directory, Staging Area y Local Repository?

El Working Directory es la carpeta del proyecto donde veo y modifico los archivos. La Staging Area es la zona intermedia donde preparo exactamente los cambios que quiero incluir en el siguiente commit. El Local Repository es el historial de commits guardado por Git dentro de la carpeta .git.

Por ejemplo, si modifico README.md, primero el cambio está en el Working Directory. Con `git add README.md` pasa a la Staging Area y con `git commit` queda guardado en el Local Repository.

## 2. Si modificas un archivo pero no haces git add, ¿aparece ese cambio en tu próximo commit?

No. El commit solo guarda lo que se encuentra en la Staging Area. Si modifico un archivo pero no vuelvo a hacer `git add`, ese cambio se queda únicamente en el Working Directory y no entra en el siguiente commit.

## 3. ¿Por qué git status no mostraba las carpetas vacías de la Parte C?

Porque Git versiona archivos, no carpetas vacías. Para solucionarlo añadimos archivos `.gitkeep` dentro de las carpetas que queríamos conservar.

## 4. Explica con tus palabras qué es HEAD.

HEAD es el puntero que indica en qué branch y commit estoy trabajando actualmente. Cuando cambio de branch, HEAD pasa a apuntar a la nueva rama.

## 5. ¿Qué diferencia hay entre git switch -c y mkdir?

`git switch -c` crea una nueva branch dentro del historial de Git y cambia a ella. `mkdir` crea una carpeta física en el disco.

Lo comprobamos porque al crear `feature/customer-search` y ejecutar `ls -la` no apareció ninguna carpeta llamada `feature`. Además, al cambiar entre main y la branch, el archivo customer-search.md desaparecía y reaparecía según la rama activa.

## 6. ¿Qué representaban los marcadores del conflicto?

El contenido entre `<<<<<<< HEAD` y `=======` representaba la versión que ya tenía la branch actual, que en nuestro caso era main.

El contenido entre `=======` y `>>>>>>> fix/readme-subtitle` representaba la versión que llegaba desde la branch que estábamos intentando fusionar.

## 7. ¿Por qué no se debe usar git commit --amend sobre un commit ya subido?

Porque `--amend` reescribe el último commit y crea uno nuevo con un hash diferente. Si el commit anterior ya se había subido y otras personas lo habían descargado, se pueden producir historiales incompatibles y problemas de sincronización.

## 8. ¿Qué ocurre si borras la carpeta .git?

Se pierde la información interna del repositorio Git: historial de commits, branches, referencias y configuración local del repositorio. Los archivos del proyecto que están en el Working Directory siguen existiendo en el disco, pero esa carpeta deja de funcionar como el mismo repositorio Git.

## 9. Diferencia entre Git y GitHub.

Git es un sistema de control de versiones que funciona en mi ordenador y permite crear commits, branches, merges y consultar el historial.

GitHub es una plataforma web que aloja repositorios Git en un servidor y añade herramientas de colaboración como Pull Requests, Issues y Code Review.

## 10. ¿Por qué no se debe subir un archivo .env con contraseñas reales?

Porque las contraseñas y claves quedarían almacenadas en el historial del repositorio y podrían ser vistas o copiadas por personas con acceso. Aunque el repositorio sea privado, las credenciales no deben versionarse. Se debe usar `.gitignore` y, si una credencial se sube accidentalmente, debe rotarse.

## 11. ¿Qué significa un error non-fast-forward al hacer push?

Normalmente significa que el repositorio remoto tiene commits que mi copia local todavía no tiene. El primer comando que ejecutaría sería `git pull` para traer y combinar esos cambios antes de volver a intentar `git push`.

## 12. ¿Qué Conventional Commit usarías en cada caso?

- Añadir un índice para mejorar el rendimiento de una tabla: `perf(db): add performance index`
- Corregir una restricción mal definida: `fix(db): correct constraint definition`
- Actualizar el README: `docs: update README`
