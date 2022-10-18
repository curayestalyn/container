<img src="media\readme\black-box.png" alt="contenedores" width="60" height="60" align="right">

# Contenedores primeros pasos
## Índice 
- [Introducción](#intro)
- [Docker](#docker)

<h1 id="intro">Introducción</h1>

Primeros pasos de camino al conocimiento de contenedores.
En este repositorio se compartida diferentes formas de crear imagenes.
Ficheros de configuración para el despliegue de aplicativos compuestos mediante servicios.


<h2 id="Docker">Docker</h2>
Docker es una herramienta que nos permite de alguna manera utilizar aplicativos reales en un entorno virtualizado de forma local.


```
// Iniciar contenedor:
      docker run <-it | d> <imagen> 
        it -> contenedor se ejecuta y se accede a la consola al momento de realizar la ejecución
        d -> contenedor se ejecuta en segundo plano
        image -> nombre de la imagen obtenido de docker hub
// Detener contenedor
      docker stop <nombre | id>   
// Borrar contenedor
      docker rm <nombre | id>
// Borrar imagen 
      docker rmi <nombre | id>
```
