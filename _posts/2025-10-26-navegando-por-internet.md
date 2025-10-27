---
layout: post
title: Guía del viajero interredes
subtitle: Algunas recomendaciones para navegar por internet sin regalarse o ser spameado.
thumbnail-img: /assets/img/viajero_intergalactico.jpg
cover-img: /assets/img/viajero_intergalactico.jpg
share-img: /assets/img/viajero_intergalactico.jpg
tags: [AdBlocks, PrivacyManager, ClearURL, URL]
mathjax: true
author: Pulga
---


> Un posteo con motivación para utilizar bloqueadores de anuncios, y algunos berres.

{: .box-warning}
La presente recomendación carece de efecto vinculante y opera como mero aviso o consejo.


{: .box-success}
Recomendaciones vigentes a 26 de octubre de 2025


![](/assets/img/notbyai-es.svg)

> El siguiente posteo va dedicado a una reciente amiga Clara, que me motivó a seguir escribiendo.

# Índice
  - [Navegar por internet](#navegar-por-internet)
  - [Navegadores](#navegadores)
  - [Buscadores](#buscadores)
  - [Recomendaciones](#recomendaciones)
  - [Política](#politica)
  - [Referencias](#referencias)

Vamos a comenzar un poco "fuerte" en términos de contextos pero se irá aclarando durante la lectura.
En caso de que quieras la versión corta ir directamente al apartado de **#Recomendaciones**.


## Navegar por internet {#navegar-por-internet}

Navegar por internet es cada día más complejo, por la misma [_"enshittification"_ o _"mierdificación"_](https://es.wikipedia.org/wiki/Decadencia_de_plataformas) que plantea Cory Doctorov, y por que los servicios son "gratis" bajo la venta de datos los cuales derivan en publicidad. En el medio está la puja entre todos para ver quien se queda con la atención del usuario, sea para venderle una estafa, o para venderle un producto real. Pero básicamente entrar a internet es como estar en la terminal de transporte o en un shopping, donde pasan vendedores de todo tipo constantemente, unos más atrevidos que otros. (Este ejemplo quizás sólo valga para latinos)


## Navegadores {#navegadores}

Vamos a lo nuestro, para poder viajar por internet debemos subirnos al colectivo que nos lleva, ése es nuestro navegador.
El navegador nos va a permitir acceder y visualizar muchísimas páginas y sitios.

Algunos navegadores son:
* Chrome _(El más conocido)_
* Firefox
* Edge
* Brave
* Tor
* Safari
* Chromium

Bueno esos son algunos, hay montones, y derivados, no nos interesa conocer todos en este posteo. Cada uno tiene sus cosas y sus dueños. Pueden encontrar más información buscando en algún buscador "Comparativa de navegadores" y verán muchos cuadros y posteos al respecto. Si quieren frikiarla pueden chusmear la página de [test de privacidad](https://privacytests.org/). No porque sea más privado es mejor... recuerden que en el día a día hacemos un balanceo entre regalar datos para poder subsistir y entre cuidarnos de no regalar de más, etc.

## Buscadores {#buscadores}

Ahora sí, hablamos de utilizar un buscador recién... pero... no era de navegadores? Bueno resulta que los navegadores utilizan [motores de búsqueda](https://es.wikipedia.org/wiki/Motor_de_b%C3%BAsqueda), que son los que nos permiten encontrar cosas en internet... dado que es un mar de fuentes y posteos. Cada motor de búsqueda "indexa" distinto la información. Antes de hablar un poco más nombremos algunos motores de búsqueda de forma que sepamos de qué hablamos:
* Google
* Bing
* DuckDuckGo
* Yahoo
* Brave Search

Y hay muchos más, organizar la información fue/es un problema muy grande. Imagínense una biblioteca del tamaño de internet... la biblioteca de Alejandría tenía aprox 100.000 libros, actualmente se estima que internet es de 181 zettabytes (181 mil millones de terabytes)

Supongamos que un libro promedio digitalizado debe estar en 3MB, de forma tal que la biblioteca de Alejandría con 100.000 libros serían 300.000MB equivalentes a 300GB.

Y 1 zettabyte (ZB) = 1.000.000.000.000 GB (mil millones de terabytes).

$$\frac{181.000.000.000.000 GB}{0.3 GB}\approx 603.333.333.333 \space bibliotecas$$

Por lo que ahora creo que podemos dimensionar lo complejo de buscar algo dentro de ese bolonqui de información.

Seguimos... entonces uno puede usar el navegador X con el motor de búsqueda Y. Obviamente quienes sean de la misma empresa se recomiendan por defecto, como sea Chrome con Google. Pero cada motor va a ordenar los resultados de búsqueda de distintas formas.
A eso se le suman, en el caso de gugel, los links patrocinados. Y a todos, los resultados generados por IA.

Veamos un ejemplo de esto.

Buscando a través de DuckDuckGo:
![Resultado de una búsqueda a través de DuckDuckGo](/assets/img/ddg_search.png)

Misma búsqueda a través de Google:
![Resultado de una búsqueda a través de Google](/assets/img/gugel_search.png)

Para cambiar los motores de búsqueda suele haber algo de esta pinta:
![Imagen de barra del navegador con opciones de motores de búsqueda](/assets/img/motores_de_busqueda.png)

> Ese es el caso del navegador Firefox.

En el caso de Chrome es un poco más complejo:

![Cambiar motor de búsqueda en Chrome](/assets/img/motores_de_busqueda_chrome.png)

> Cambiar motor de búsqueda del navegador Chrome.

## Recomendaciones {#recomendaciones}

Para poder navegar sin comerse todas las publicidades y carteles que se abren sólos, se utilizan "adblockers" osea **"bloqueadores de anuncios"**, recomiendo [uBlockOrigin](https://ublockorigin.com/), el cual es un complemento del navegador, que tiene muchas listas de sitios que están denunciados por spam, etc, de forma tal que filtra todo eso y evita que se abran o te sugiere no acceder a algunos. Además se pueden agregar filtros, desactivar o activar algunas funcionalidades extras, dado que a veces uno sí quiere que se abran algunos paneles, etc. Con esto no te vas a comer anuncios en yutube, evitas posibles clicks en cualquier lado, o que se te abran 34 pestañas sin que vos quieras, y ni hablar de no entrar en carteles falsos. Para no tener anuncios en yutube tmb hay un "youtube tuneado" que se llama [yewtu.be](https://yewtu.be/).

Luego para "privacidad" está [Privacy Badger](https://privacybadger.org/#What-is-Privacy-Badger) el cual va a evitar que nos "rastreen" las páginas que visitamos... esto como sucede? bueno... cuando le damos a "aceptar todas las cookies" ahí nos guardan "galletitas/cookies" en nuestro navegador, y se puede ir siguiendo la navegación, esto permite realizar una publicidad más personalizada, etc.

Hablando de Cookies... y lo último que menciono

![Cartel de cookies de la página de F1](/assets/img/cookie_F1.png)


Los botones más faciles de clickear son "aceptar todo", pero si nos tomamos un ratito, siempre habrá un "gestionar ajustes", el cual nos permite no aceptar todo, de forma de evitarnos algunos trackeos, manejo de publicidad y que se nos acumulen cookies en el navegador.


## Política {#politica}

Sobre todo esto, en profundidad con contexto y sobre todo el mercado que es realmente un buscador, escribe el grandísimo [Juan Brodersen en su newsletter Dark News](https://www.brodersendarknews.com/p/google-ads-monopolio-impacto-usuario). 
Rescato una parte de la nota de Juan donde menciona lo siguiente:

> _"...Y no es menor el ataque a esta parte del negocio de Alphabet, empresa matriz de Google: es el core de su modelo. De los casi 320.000 millones de dólares en ingresos anuales de Alphabet en 2024, más de 250.000 millones vinieron de publicidad._
_En total, alrededor del 78% de los ingresos totales de Alphabet ese año provinieron del negocio publicitario, entre Google Search (búsqueda), avisos en YouTube y los anuncios de terceros a través de AdSense y Ad Manager."_

Además lo que es curioso es que los anuncios se venden en el Ad exchange de Google Ad Manager, por lo que Gugel es vendedor y comprador. Por eso es que ha sido acusado de monopólico.

De esta forma podemos visualizar porqué es tan importante un buscador, porqué son tan densos con meter cookies y con que aceptes todas sus políticas de cookies.

Además los chatbots de IA han duplicado la información falsa, y muchos de los usuarios nos sentimos satisfechos con nuestra búsqueda cuando nos responde un chatbot... el cual... alucina... entonces ahora es un doble trabajo el de chequear:
1. Que el chatbot no alucine.
2. Que los links no sean links que están arriba por patrocinio, osea pagos.
3. Que los links que mayor ponderen tengan buena información.

Y ni hablar que en el caso **2.** los links patrocinados pueden ser links de "phishing" osea "estafas", esto es mencionado por Juan en la charla citada en las referencias en el minuto 31:56.

Y por último considerar gastos energéticos y de refrigeración que pueden realizar dichas tecnologías. Dado que una búsqueda ya de por sí puede llevar mucho cómputo, y sumándole la IA aumenta, y todo eso genera calor, como en la compu de tu casa, así que para eso se usa agua para refrigerar. Acá no hay mucha data precisa porque los gigantes tecnológicos no son muy transparentes. Dejo en las referencias el blog de "Tu Nube Seca Mi Río" quienes trabajan sobre estas temáticas.

## Referencias {#referencias}

* [DarkNews](https://www.brodersendarknews.com/p/google-ads-monopolio-impacto-usuario)
* [Información Falsa IA](https://www.brodersendarknews.com/p/desinformacion-chatbots-ia-chatgpt-gemini)
* [Cyberseguridad y Periodismo - Charla Juan Brodersen](https://youtu.be/qS3J1QigqFo)
* [Tu Nube Seca Mi Río](https://tunubesecamirio.com/)