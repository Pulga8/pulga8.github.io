---
layout: post
title: Sanitizar URLs
subtitle: Qué son las URLs y como cuidar al compartir posts.
thumbnail-img: /assets/img/ga4.png
share-img: /assets/img/ga4.png
tags: [Sanitizar, URL, ClearURL, Sanitize, Sanitization URL]
author: Pulga
---

{: .block-tip}
Sanitizar URLs no es un consejo de privacidad propiamente, el fin de este post es concientizar sobre las URLs para un poco entender ¿qué son? y que dicha información nos permita diferenciar URLs falsas de originales, y identificar qué parte de la URL no es necesaria y es sólo para publicida.

![](/assets/img/notbyai-es.svg)

# Qué es una URL?

Bueno básica y sencillamente es una **dirección** tal como conocen, que al poner en el navegador, nos muestra una página web, imágen, etc. Viene del acrónimo de "Uniform Resource Locator", sí todo en inglés.

Por ejemplo: *www.google.com* es una **URL**. Y así todas las que se les ocurran.

La URL es compuesta por distintas partes, cada parte tiene un sentido, explicar esto es un poco más largo y técnico, lo haremos más adelante.

Seguimos!

# Qué es sanitizar y porqué?

Sanitizar una URL es lo que pensabas, es limpiarla, quitarle las partes que "ensucian" la dirección. Recortar partes del texto que no son necesarias, ya que llegaremos a la misma página.

Seguro suenan algunas preguntas como: ¿Che pero porqué hay partes que ensucian? Si no me sirven para qué están?

Aguantamos y ahí tratamos de responder.

Seguimos!

# Anatomía de una URL y Códigos de Trackeo

Tomemos esta URL:

> https://www.amazon.com/gp/help/customer/display.html?nodeId=508510&ref_=nav_cs_customerservice

Separemos esto para enteder qué es cada cosa:

```
https://                            --> (Protocolo de Internet)
www                                 --> (Sub-Dominio)
amazon.com                          --> (Dominio)
/gp/help/customer/display.html      --> (Ruta al archivo)
?                                   --> (Separador)
nodeId=508510                       --> (Código de seguimiento)
&                                   --> (Separador de consulta)
ref=nav_cs_customerservice          --> (Código de seguimiento)
```

Bueno hasta el separador **'?'** es el núcleo de la URL, esa es la parte clave, que nos lleva hasta el recurso que querramos, foto, página web, etc.
Lo que sigue luego de ese separador, son todos parámetros extra que en muchos casos son de manejo propio de cada servicio. Por ejemplo Google Analytics, está incoporado en muchísimas de las páginas que visitamos, permite llevar un conteo de todo, cantidad de clicks en la página, locaciones desde donde se visita la página, etc. Para eso utiliza "trackers" osea "seguimientos" no sé cuál sería la perfecta traducción, básicamente te rastrea la navegación a través de ese pendorcho que te deja en la URL.

Los más conocidos son los [UTM(Urchin Tracking Module)](https://es.wikipedia.org/wiki/Par%C3%A1metros_UTM), "módulos de seguimiento Urchin".

Algunos parametros para "trackear/seguir":
* `utm_id`: ID de campaña, identifica una campaña de anuncios en particular.
* `utm_source`: Identifica al anunciante, sitio, publicación, etc. A quién envía info por ejemplo: google, newsletter4, billboard.
* `utm_medium`: Identifica el medio por el que llega el tráfico, como email o costo por click. Esto te permite ver qué campaña tuvo más éxito, si la de mail, etc.
* `utm_campaign`: Se utiliza para identificar un producto en específico o una promoción.
* `utm_term`: Términos de búsqueda. Palabras clave de las publicidades.
* `utm_content`: Este refiere a de donde venís, por ejemplo de haber clickeado un popup o un banner, etc.

Ahora veamos un ejemplo:

> https://www.ejemplo.com/page?utm_content=buffercf3b2&utm_medium=social&utm_source=facebook.com&utm_campaign=buffer

Entonces si quisieramos sanitizar dicha URL, ya sabemos pará que sirven muchos de esos pendorchos que se meten en la URL.
Si la sanitizaramos quedaría:

> https://www.ejemplo.com/page

Podés dejar de leer acá, pero te vas a quedar sin saber porqué sacarlas.

{: .box-warning}
No todo lo que va después del **?** hay que sacar, algunas veces lo que va después del separador, sirve para identificar el posteo o la página. A medida que sanitizen URLs se irán dando cuenta.

Sigamos!


# Porqué sacarlas?

Bueno, retomando con la URL de Amas*n:

> https://www.amazon.com/gp/help/customer/display.html?nodeId=508510&ref_=nav_cs_customerservice

Cuando compartis ese enlace por wpp o la red social que uses, estás haciendo que la persona que haga click en dicho enlace se vincule con vos, de forma tal que ayuda a la campaña de márketing pero también modifica las recomendaciones de la persona, y también estamos compartiendo datos nuestros, sobre qué campaña estuvimos viendo, etc.
Entiendo a casi nadie le importa regalar datos, entonces no lo hagan por los datos, haganlo para no "modificar" su algoritmo o el de otra persona.
Si sanitizamos la URL compartida podrán ver que nos redirecciona a la misma página:

> https://www.amazon.com/gp/help/customer/display.html

Claramente esto no es realmente un consejo de privacidad dado que existen Cookies, y demás cosas que alojan monton de datos, pero al menos creo que entender esto concientiza sobre el uso de URLs y espero sirva para comenzar a prestar atencion a las URL y en un futuro que permita identificar páginas falsas, noticias falsas, "scam" osea fraudes, y demás basofia que anda dando vueltas.

No todo lo que va después del **?** se debe quitar, pero se irán dando cuenta a medida que recorten URLs.

# Ejemplos de URLs

Tomando el video "Linus Torvalds Guided Tour of His Home Office"
Veamos su URL... pero esperá... la URL del navegador? la que me aparece arriba? o la del botón de "Share/Compartir" ?

Veamos primero la "de arriba":

> https://www.youtube.com/watch?v=jYUZAF3ePFE

Okay descompongamos como aprendimos:

```
https://                            --> (Protocolo de Internet)
www                                 --> (Sub-Dominio)
youtube.com                         --> (Dominio)
/watch                              --> (Ruta al archivo?)
?                                   --> (Separador)
v=jYUZAF3ePFE                       --> (Que leches es esto?)
```
Okay si borramos lo que sigue luego del separador **?**, nos quedaría sólo `https://www.youtube.com/watch` pueden probar acceder a ese link pero no va a nuestro video simplemente redirecciona a la página principal de yutu. Entonces? bueno acá podemos ver a qué me refería con el warning ése de más arriba, en este caso el `v=jYUZAF3ePFE` hace referencia al id (un código de identificación) de nuestreo video, pueden pensarlo como `video=jYUZAF3ePFE` entonces completando la ruta estaríamos diciendo *"Yutu quiero ver el video jYUZAF3ePFE"* algo así sería lo que se traduciría esa URL en formato de juego `youtube.com/watch?v=jYUZAF3ePFE`
En este caso no hay nada que sanitizar.

Veamos el botón de "Share/Compartir":

> https://youtu.be/jYUZAF3ePFE?si=yGBBNd-nE4nsxK5y

Observen como cambió, ahora es **youtu.be** el dominio, por más que es un link de nuestro conocido **youtube.com**, también notar que se repite el "identificador del video":`jYUZAF3ePFE`. Ahora en este caso, sí todo lo que va después del separador **?** no sirve para nada.
Por lo tanto en caso de querer sanitizarla quedaría:

> https://youtu.be/jYUZAF3ePFE

### Y voilà, ya sabemos sanitizar o limpiar URLs.

Miren las URLs de mercado livre lo largas y el chorizo de giladas que tienen...

Les dejo un meme en inglés y su traducción por las dudas:

![](/assets/img/meme_sanitizar.jpg)
> Esta imagen es cortecía de [@campfireharve.st](https://bsky.app/profile/campfireharve.st)

![Traducción](/assets/img/meme_sanitizar_traducido.png)


Saludos Vaqueros de internet...

# Referencias

- [GA4](https://ga-dev-tools.google/ga4/campaign-url-builder/)
- [URL Sanitization — The Why and How](https://faun.pub/url-sanitization-the-why-and-how-9f14e1547151)
- [Paginación con rel="next" y rel="prev" - Google Developers](https://developers.google.com/search/blog/2011/09/pagination-with-relnext-and-relprev?hl=es)
- [Reglas de Sanitización Navegador Brave](https://raw.githubusercontent.com/AdguardTeam/FiltersRegistry/master/filters/filter_17_TrackParam/filter.txt)
- [Posteo consulta sobre complementos que hagan esto automágicamente](https://orionfeedback.org/d/4375-remove-trackers-from-copied-urls)