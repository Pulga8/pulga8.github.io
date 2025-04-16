---
layout: post
title: Mastodon desde la terminal
subtitle: Usando Toot para ver Mastodon
cover-img: /assets/img/toot1.jpg
gh-repo: ihabunek/toot
gh-badge: [star, fork, follow]
tags: [CLI, Mastodon, Terminal, Bash]
comments: true
mathjax: true
author: Pulga
---

{: .box-warning}
Este es un posteo de aprendizaje y de prueba, no debe ser usado como guía técnica. Para ver detalles técnicos está la [documentación oficial de toot](https://toot.bezdomni.net/).
Por las dudas mencionar que hace falta una cuenta en alguna instancia de mastodon para usar esta herramienta.


## Toot

Toot es un cliente de [Mastodon](https://mastodon.social/) desde la línea de comandos, o terminal. Permite interactuar con instancias de Mastodon, con una interfaz muy liviana desde la consola.

Lo único no tan sencillo es el tema de las imágenes, pero se habla sobre éso [acá](https://github.com/ihabunek/toot?tab=readme-ov-file#tui-features) y no tienen realmente un inconveniente.

<details markdown="1">
<summary>Ver más sobre Mastodon</summary>
[Documentación de Mastodon.](https://docs.joinmastodon.org/)
</details>

Probé esta herramienta desde un [Antix](https://antixlinux.com/) modificado, conocido como [Cirujantix](https://cybercirujas.rebelion.digital/foro/viewtopic.php?t=324) ya que es un Antix modificado por el grupo Cybercirujas :)

## Instalemos Toot

Hay varias formas de instalar toot, yo usé apt-get si mal no recuerdo.

1. Actualizamos:
  ```sh
  $ sudo apt-get update
  ```

2. Instalamos
  ```sh
  $ sudo apt-get -y install toot
  ```

<details markdown="1">
<summary>Desinstalar</summary>
Para desinstalar usar:
```sh
$ sudo apt-get remove toot
```
Y eliminar toot y sus dependencias:
```sh
$ sudo apt-get -y autoremove toot
```
</details>

> También se puede instalar vía pip, apt, brew y demás, en la documentación están bien especificados los métodos o formas.

## Bueno vamo' a tootear

Una vez instalado debemos iniciar sesión, para esto está el comando:

```sh
$ toot login
```

Nos devolvera algo de la pinta:

~~~
$ toot login
Enter instance URL [https://mastodon.social]: https://rebel.ar
Looking up instance info...
Found instance Mastodon running Mastodon version
Registering application...
Application tokens saved.

This authentication method requires you to log into your Mastodon instance
in your browser, where you will be asked to authorize toot to access
your account. When you do, you will be given an authorization code
which you need to paste here.

This is the login URL:
https://rebel.ar/oauth/authorize/?response_type=code&redirect_uri=urn%3Airt%3Bwg%2Aoauth%32.0%3Aoob&scope=read+write+follow&client_id=RANDOMHASH

Open link in default browser? [Y/n]Y
Authorization code: Se está abriendo en una sesión de navegador existente.
~~~

> El mensaje anterior tiene cosas borradas, pero de aparecerles sería casi igual.

A lo cual seguimos el link como en cualquier método de inicio de sesión.
Esto nos lleva al navegador donde nos pedirá darle acceso de lectura, escritura, seguimientos, silenciados, bloqueados, y no recuerdo si algo más. Y tiene sentido que pida estos permisos, ya que tiene que poder hacer dichas cosas, esto es, vamos a querer tootear desde esta herramienta, leer toots, y demás opciones.

Luego de esto nos aparece el código de autentificación, para autorizar justamente al cliente toot a usar mastodon.

Pegamos el código en la terminal:

~~~
Authorization code: Se está abriendo en una sesión de navegador existente.
aAeUoyYWQlXxTB9lYOV-yhocIrZ3-bGKlpBL-LYtNAN2FvR

Requesting access token...
Access token saved to config at: /home/joan/.config/toot/config.json

✓ Successfully logged in.
~~~

¡ENTRAMOS! :)

I'm in diría Neo.

<details markdown="1">
<summary>Cerrar sesión</summary>
Para cerrar la sesión creo que era así:

```sh
$ toot logout usuario@instancia
```
o agregando comillas así, no recuerdo:

```sh
$ toot logout "usuario@instancia"
```
</details>

Ahora nos disponemos a abrir la interfaz gráfica de toot:

```sh
$ toot tui
```

Se nos abrirá la interfaz y vamos a poder navegar entre toots, escribir toots, poner estrellitas, etc.

### Ejemplo

Tooteando desde Toot

Para escribir un toot apretamos la letra **C**

Nos abrirá una "sobrepantalla" o como quieran decirle, con las opciones de escribir, publicar el toot, y un par de ajustes.
Escribimos  nuesto toot con la famosa entrada "Hola desde..."

![Toteando](/assets/img/toot3.png)

Le damos a la opción de publicar _'Post'_ y al tootear:

![Toteando](/assets/img/toot4.png){: .mx-auto.d-block :}

Y charan! Ya vemos nuestro toot publicado, hay muchos atajos de teclado para realizar distintas acciones, no voy a ponerlos acá pero pueden verlos en la documentación citada en el inicio del post.


## Antes de irnos

Algo que está muy bueno es poder usar toot desde "afuera" (Capita de abstracción :sunglasses: ahora sí 🕶️), la herramienta tiene varios comandos, acá sólo se usaron `login` y `tui` pero hay muchos más, de hecho pueden verlos con `$ toot --help`.

Por ejemplo:

```sh
# Enviar un toot que diga "Hola desde toot"
$ toot post "Hola desde toot"
```
```sh
# Enviar un toot con salto de línea
$ toot post "$(echo -e "Hola\nDesde toot")"
```
```sh
# Ver las notificaciones
$ toot notifications
```
```sh
# Ver los últimos cinco toots del la línea de tiempo.
$ toot timeline --count 5
```

De esta forma, hasta se podrían calendarizar toots, ya que con el gran `cron` o cualquier método de ejecución por fecha de este comando, alguna cola de tareas, etc, permitiría dejar un toot para que se publique en algún día y hora que se quiera.

Lo usé en una compu con 2 cores y 2Gb de ram, y obviamente jamás me anduvo lento ni nada.

Es parte quizás y ayuda a una web liviana, y da la posibilidad a interactuar con Mastodon con escasos recursos, sin necesidad de abrir un navegador.