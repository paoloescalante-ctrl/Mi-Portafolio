# Guía del Laboratorio 02: Ramas, Merge y Conflictos

Esta guía documenta mi **Laboratorio N° 2** del curso de Diseño de Interfaces de Programación Avanzado en Tecsup. Donde te explicare como se crean ramas, merge y que conflictos se pueden generar.

![Captura del trabajo en Visual Studio Code](../img/image1.png)

## ¿De qué trata el proyecto?

Es una página web mínima de dos archivos sobre la que se practica el trabajo con ramas en Git. El objetivo es aprender a:

- Crear ramas y trabajar en ellas sin afectar la rama principal.
- Distinguir un merge automático (fast-forward) de uno con conflicto.
- Provocar un conflicto de forma controlada, leerlo y resolverlo a mano.
- Marcar una versión estable con una etiqueta (tag) y publicarla en GitHub.


El repositorio con el historial completo está en [lab02 en GitHub] (https://github.com/paoloescalante-ctrl/lab02.git) 

## Cómo reproducirlo

### Requisitos

Necesitas Git instalado (comprueba con `git --version`), Visual Studio Code y una cuenta de GitHub. 
### Pasos

1. Crea la carpeta del proyecto, inicializa Git y crea los archivos `index.html` y `estilos.css`.
2. Haz el primer commit en `main` con el título del proyecto en color `gray`.
3. Crea la rama `menu` con `git checkout -b menu`, agrega un menú de navegación y fusiónala (sale como fast-forward).
4. Crea la rama `color-azul` desde `main` y cambia el color del título a azul.
5. Vuelve a `main` y crea la rama `color-rojo`, cambiando la **misma línea** a rojo.
6. Fusiona `color-azul` y luego `color-rojo`: el segundo merge produce el conflicto.
7. Resuelve el conflicto en `estilos.css`, ejecuta `git add estilos.css` y cierra con un commit.
8. Marca la versión con una etiqueta y publícala en GitHub.

```bash
git switch main
git merge color-rojo
git add estilos.css
git commit -m "Resuelve conflicto de color del titulo"
git tag -a v1.0 -m "Version estable del laboratorio 02"
git push origin main
git push origin v1.0
```

## Archivos y comandos importantes

| Archivo o comando | Qué hace |
|-------------------|----------|
| `index.html` | Página principal con el título, el menú y el pie de página |
| `estilos.css` | Estilos de la página; contiene la línea del color que provoca el conflicto |
| `git merge --abort` | Cancela un merge en curso y vuelve al estado anterior |
| `git log --oneline --graph --all` | Dibuja el historial de ramas con todos los commits |
| `git push origin v1.0` | Publica la etiqueta, porque un `git push` normal no la sube |

## Estado del trabajo

- [x] Repositorio publicado en GitHub con el historial de la parte guiada
- [x] Commit de resolución del conflicto visible en el historial
- [x] Rama `pie-pagina` creada, fusionada a `main` y borrada
- [x] Etiqueta `v1.0` publicada en el repositorio remoto
- [ ] Publicar la página con GitHub Pages