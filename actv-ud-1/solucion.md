# Tema 1: Git

## Ejercicio 1 — Primer repositorio git

Repositorio `biblioteca` con `README.md`, `.gitignore` y `datos/notas.txt`,
añadidos en tres commits separados.

### Historial final

```console
$ git log --oneline
3d2dd88 (HEAD -> main) Add initial library project notes
648fbe7 Add ignore rules for system and temporary files
fdd4fe8 Add project README
```

## Ejercicio 2 - Trabajo con ramas

Creadas dos ramas de funcionalidades, con dos commits en cada una, y fusionadas en `main` utilizando `--no-ff`.

### Historial final

```console
$ git log --oneline --graph --all
*   4193743 (HEAD -> main) merge user management feature
|\
| * 19caccf (feat/gestion-usuarios) add sample user password
| * 792c7eb add user name and email
* |   3ab4b3b merge book management feature
|\ \
| |/
|/|
| * bc3a382 (feat/gestion-libros) add book ISBN field
| * e1509a6 add book title and author
|/
* 3d2dd88 Add initial library project notes
* 648fbe7 Add ignore rules for system and temporary files
* fdd4fe8 Add project README
```

## Ejercicio 3 — Resolución de conflictos

He modificado la misma línea de `mensaje.txt` en `main` y en
`feat/nuevo-saludo`, provocando un conflicto al fusionar.

```console
$ git merge feat/nuevo-saludo
CONFLICT (content): Merge conflict in mensaje.txt
Automatic merge failed; fix conflicts and then commit the result.
```

### Resultado

```console
$ cat mensaje.txt
Hola mundo!

$ git status
On branch main
nothing to commit, working tree clean
```

### Historial final

```console
$ git log --oneline --graph --all
*   8ed7589 (HEAD -> main) resolve greeting conflict keeping main message
|\
| * 98f7177 (feat/nuevo-saludo) update message in feature branch
* | 3d17882 update message in main
|/
* bd3ab6f add initial greeting
```

## Ejercicio 4 — Simulación de Git Flow

He trabajado con las ramas `main` y `develop`, desarrollado el carrito
en `feat/carrito-compra` y preparado la versión `v1.0` mediante
`release/1.0`.

Después he corregido el precio de la pantalla en `hotfix/error-precio`,
integrando la corrección en `main` y `develop` y creando la etiqueta
`v1.0.1`.

### Historial final

```console
$ git --no-pager log --oneline --graph --all
*   0ae79b1 (HEAD -> develop) merge price hotfix to dev
|\
* \   3508675 merge release 1.0 to dev
|\ \
| | | *   bf62c65 (tag: v1.0.1, main) merge price hotfix to main
| | | |\
| | | |/
| | |/|
| | * | 1256ca5 (hotfix/error-precio) fix screen price
| | |/
| | *   e140283 (tag: v1.0) merge release 1.0 to main
| | |\
| | |/
| |/|
| * | e82db76 (release/1.0) release 1.0
|/ /
* |   fcf27cf merge cart feature
|\ \
| |/
|/|
| * 952e541 (feat/carrito-compra) add second item
| * 3fba68b add first item
|/
* 8463e39 add store project README
```
