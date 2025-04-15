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


## Toot

Toot es un cliente de Mastodon desde la línea de comandos, o terminal. Permite interactuar con instancias de Mastodon, con una interfaz muy liviana desde la consola.

Probé esta herramienta (tool) desde un [Antix](https://antixlinux.com/) modificado, conocido como [Cirujantix](https://cybercirujas.rebelion.digital/foro/viewtopic.php?t=324) ya que es un Antix modificado por el grupo Cybercirujas.

## Instalemos

Hay varias formas de instalar toot, yo usé apt-get.

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

También se puede instalar vía pip, apt, brew y demás, en la documentación están bien especificados los casos.

![Toteando](/assets/img/toot3.png)

Y al tootear:

![Toteando](/assets/img/toot4.png){: .mx-auto.d-block :}

<!-- Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.

## Local URLs in project sites {#local-urls}

When hosting a *project site* on GitHub Pages (for example, `https://USERNAME.github.io/MyProject`), URLs that begin with `/` and refer to local files may not work correctly due to how the root URL (`/`) is interpreted by GitHub Pages. You can read more about it [in the FAQ](https://beautifuljekyll.com/faq/#links-in-project-page). To demonstrate the issue, the following local image will be broken **if your site is a project site:**

![Crepe](/assets/img/crepe.jpg)

If the above image is broken, then you'll need to follow the instructions [in the FAQ](https://beautifuljekyll.com/faq/#links-in-project-page). Here is proof that it can be fixed:

![Crepe]({{ '/assets/img/crepe.jpg' | relative_url }})

<details markdown="1">
<summary>Click here!</summary>
Here you can see an **expandable** section
</details> -->
