---
layout: post
title: IA y Demás Yuyos
subtitle: Desmenuzando la inteligencia artificial
date: 2025-12-27
thumbnail-img: /assets/img/ia_yuyos.jpg
cover-img: /assets/img/ia_yuyos.jpg
share-img: /assets/img/ia_yuyos.jpg
categories: [technology, ai]
tags: [IA, LLM, DeepLearning, Transformers]
description: "Una descripción pequeña y generalista sobre la IA"
image: /assets/images/ia-demas-yuyos.png
image_alt: "Inteligencia Artificial"
keywords: inteligencia artificial, IA, DeepLearning, NN
toc: true
comments: true
share: true
excerpt: "Una descripción pequeña y generalista sobre la IA"
lang: es
robots: index, follow
mathjax: true
canonical_url: https://pulga8.github.io/technology/ai/ia-y-demas-yuyos/
reading_time:
author: Pulga
---

> Trataremos de desmenuzar chuncanamente algunos conceptos de la IA. No por ello es un posteo liviano, de hecho es largo, pero espero que quien lo lea se lleve una visión un poco más iluminada de la caja negra que es la IA.

{: .box-warning}
Este es un posteo de aprendizaje y de prueba, no debe ser usado como guía técnica y puede estar sujeto a errores. Es un posteo generalista por lo que muchos conceptos pueden no ser del todo correctos, dado el recorte realizado para poder leerse en un sólo post y con intención de que sea legible para cualquiera.

![](/assets/img/notbyai-es.svg)

## IA

Arranquemos, la IA se llama así "inteligencia artificial" por una cuestión filosófica donde para no ligarla a la inteligencia humana, le pusieron artificial. (Entiéndase esto escrito de forma burda y expres, hay muchísimo de porqué se llama así y de si está bien o no, y demás debate) Pero por más que haga cosas increíbles sigue siendo una enorme función probabilística que realiza millones de cálculos en poquísimo tiempo generando texto, imágenes, o videos, que parecieran "reales" por una cuestión de que son construcciones realizadas en base a lo más probable.

Tenemos 3 tipos de "IA":

1. **Artificial Narrow Intelligence (ANI) - Inteligencia Artificial Estrecha**  
   La IA que conocemos, sistemas de recomendación como "el algoritmo de netflis", chatgpt, etc.

2. **Artificial General Intelligence (AGI) - Inteligencia Artificial General**  
   Es teórica al día de hoy.

3. **Artificial Super Intelligence (ASI) - Superinteligencia Artificial**  
   Teórica al día de hoy.

Hay más divisiones, dependiendo distintos aspectos.

<details>
<summary>Ver otros tipos de IA</summary>
<div markdown="1">

### Por Tipo de Salida

Por ejemplo también puede ser clasificada dependiendo su salida (lo que escupan los bichos estos).

| Tipo           | Ejemplo                                    |
| -------------- | ------------------------------------------ |
| Predictiva     | Predicción de demanda                      |
| Clasificatoria | Diagnóstico                                |
| Generativa     | Texto / imagen (chatgpt, deepseek, etc.)   |
| Prescriptiva   | Qué acción tomar                           |
| Descriptiva    | Análisis de datos                          |

![Diagrama de la IA](/assets/img/diagrama_ia.png)
> Imagen sacada del post ["Introducción a la IA"](https://substackcdn.com/image/fetch/$s_!ZN81!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6a19d544-41e2-4eea-ba75-2abbec92d261_4000x2530.png)

Dentro de las ANI podemos dividirlas dependiendo como se las "entrene":
* Supervised
* Unsupervised
* Semi-supervised
* Reinforcement learning

> No sabemos aún qué es entrenar pero bueno, ya lo veremos más adelante.
</div>
</details>

## Pequeñísimo repaso de historia

![Historia de la IA](/assets/img/historia_ia.jpg)
> Imagen tomada del curso "How Transformer LLMs Work" - Jay Alammar, DeepLearning.ai

Donde podemos ver distintos tipos de LLMs.
* Decoder-only (GPT)
* Encoder-only (BERT)
* Encoder-Decoder (T5)

<details>
<summary>Otra forma de clasificarlos según su arquitectura</summary>
<div markdown="1">

* Auto-regressive (GPT)
* Auto-encoding (BERT)
* Sequence-to-sequence (T5)
</div>
</details>

Estas diferencias de "Sólo Decodificador", "Sólo Codificador" y "Ambos", son diferencias de **Arquitectura**, osea cómo fueron construidos. *Retomaremos esto más adelante*.

![Arquitecturas de tranformers, encoder-only, decoder-only y encoder-decoder](/assets/img/tranformers_arq.png)
> Fuente: [DailyLifeAi](https://daily-life-ai.com/251/)

Por lo tanto podemos ver que son parecidas en algunas cosas pero claramente distintas, y una parece una unión de las otras.

## Vamos a lo nuestro

Hay una rama dentro de la IA que es llamada Machine Learning (Aprendizaje Automático), dentro de esta rama se encuentra otra rama llamada Deep Learning (Aprendizaje Profundo), y dentro del Deep Learning está la IA Generativa, que es la que utilizamos.

ANI → Machine Learning → Deep Learning → Generative AI.

> No todo el machine learning es generativo, no todo deep learning es generativo. **La Ia generativa es un tipo de modelos de Deep Learning.**

Lo que más usamos son LLMs, grandes modelos de lenguaje, tales como Claude, ChatGPT, que son un tipo de IA Generativa. Al decir LLM hacemos referencia a lo que se llama "modelo". ChatGPT y Claude son más que sólo un modelo, porque son aplicaciones, dentro de ellas podés elegir distintos modelos, y hacer más cosas.

Se puso jodido el post pero es complejo comentar estas cosas, y además peco de poner cosas "simplificadas" con cosas "complejas" haciendo un posteo generalista.

Analizaremos sobre un LLM GPT (Generative Pre-Training), osea un modelo de IA Generativa que es decoder-only, dado que citaremos una [página](https://bbycroft.net/llm) que está muy linda, que permite ver uno paso a paso.

| Arquitectura Decoder-only | Arquitectura NanoGPT |
|---|---|
| ![Transformer Decoder-only](/assets/img/decoder_only.png) Fuente: [DailyLifeAi](https://daily-life-ai.com/251/) | ![NanoGPT](/assets/img/nano_gpt.png) Fuente: LLM Visualization|

> Observemos que la web nos muestra exactamente un decoder-only, donde en la imagen de la izquierda se inicia desde abajo, y en la de la derecha se inicia desde arriba, está la diferencia del Multi-Head Attention, antes de la etapa de FeedForward, pero debe ser alguna modificación de optimización de NanoGPT.

Por lo que podemos ver que nuestro posteo será hablar de sus etapas:

1. Tokenizer/Embedding
2. Normalización
3. Self Attention
4. MLP
5. Softmax
6. Output


### Lo primero: Tokenizer/ Embedding

La máquina no entiende como nosotros, por lo que para "entender" necesitamos partir el texto ingresado. Cada "IA" parte el texto en distintas formas. Pueden jugar ingresando distintos textos en el [Tokenizer de OpenAI](https://platform.openai.com/tokenizer) y ver cómo se "tokeniza"/"recorta" dependiendo el modelo.

Por ej:

| Modelo | Tokenización |
|--------|--------------|
| GPT-4o | ![Tokenizador con la frase "Es una locura vivir con miedo, ¿no? Eso es ser esclavo."](/assets/img/tokenizer_1.png) |
| GPT-3 | ![Tokenizador con la frase "Es una locura vivir con miedo, ¿no? Eso es ser esclavo."](/assets/img/tokenizer_2.png) |


{: .block-tip}
Así es, a partir de ahora introducimos el concepto de **tokens** que son las divisiones que hará cada modelo para poder "entender" nuestras frases. En criollo recortes de nuestra frase.

<details>
<summary>Ver otros tipos de tokenización</summary>
<div markdown="1">

* Tokenización basada en palabras (Word tokenization)
* Tokenización basada en subpalabras (Subword tokenization)
* Tokenización basada en caracteres (Character tokenization)
* Tokenización basada en símbolos (Symbol tokenization)
* Tokenización basada en frases o unidades lingüísticas más grandes (Phrase tokenization)
* Byte-level BPE (a nivel de bytes), como usa GPT-2
* WordPiece, usado por BERT

> Se puede ver y leer mucho más sobre esto en el [Curso de LLMs de Hugging Face](https://huggingface.co/learn/llm-course/es/chapter2/4)
</div>
</details>


La misión ahora es tratar de tener en cuenta cada pedacito recortado, para más facilidad utilizemos "Tokenización basada en palabras" donde cada token representa una palabra, como vimos debemos convertir cada palabra en un "token".
Luego convertiremos cada pedacito o token en un vector numérico y lo llamaremos *Embedding*. Para diferenciar cada token se usan los Token Embeddings y para saber información acerca del órden que aporta cada palabra se usan los Positional Embeddings. Ya que la compu no sabe (La arquitectura usada no sabe por sí mismo cuál es el órden de un token en la secuencia de tokens).
Entonces para cada token hay un "Token Embedding", "Position Embedding", que cada uno representan: El token en sí, y el órden que ocupa el token en la frase.

Porqué necesitamos el orden?

No es lo mismo decir: "Mañana tengo que ir al banco a sacar plata."

Que decir: "Plata a sacar banco ir al mañana tengo"

Por lo que es necesario "recordar" con los Position Embeddings el orden de las palabras en la frase. (Coherencia)
Recordemos que todo esto está basado fuertemente en la lingüística.

Tomemos una palabra como ejemplo:

**Entrada:** "Maradona"

**Proceso:**
1. Tokenización → `token = "Maradona"`
2. Asignación de ID → `token_id = 18427`
3. Conversión a embedding → `embedding = [0.91, -0.33, 1.27, 0.08, -0.54, 0.62]`

**Resultado:**
- **Token:** qué palabra es ("Maradona")
- **Token ID:** identificador numérico único (18427)
- **Embedding:** representación vectorial numérica de la palabra

El modelo no entiende de tokens, sólo entiende de embeddings.

Sucede una gran magia en los embeddings que es media compleja asi que no la explicaremos acá, pero esa transformación a un vector seguro les pierda porque falta explicar una parte, pero quedense con lo visto.

* Token Embedding: va a representar qué es "Maradona", y se va a ir recalculando.
* Positional Embedding: va a representar dónde está el token en la frase.

Buscamos entonces sumar ambos vectores generando así el **Input Embedding**.

$$\text{Input Embedding} = \text{Token Embedding} + \text{Positional Embedding}$$

Como si fuera ArtAttack nos quedaremos con este resultado sacado sin fundamento, pero para que se vea qué es lo que se enviará a la primer etapa del tranformer.

Input embedding ("Maradona", posición 0) = [ 0.93, -0.18, 1.16, 0.48, -0.47, 0.53 ]


![Embedding "work" comparado con muchas palabras, en concreto la imagen muestra el comparativa con la palabra "went"](/assets/img/embedding.png)
> Fuente: [Generative AI](https://ig.ft.com/generative-ai/)

Como podemos observar en la parte inferior de la imagen la palabra work y su embedding asociado, que tiene los valores comparados contra la palabra "*went*"

![Embeddings de palabras relacionadas](/assets/img/similar_embedding.png)
> Fuente: [Generative AI](https://ig.ft.com/generative-ai/)

En esta imagen podemos ver como palabras como "sea" (mar) y "ocean" (océano) tienen embeddings parecidos porque representan cosas similares y así con otros ejemplos.

{: .block-tip}
Ahora ya sabemos que los "Embeddings" son los tokens vectorizados, osea los tokens convertidos en vectores de números, que nos permiten capturan la información semántica y sintáctica de las palabras que representan.

### Normalización

Hasta el punto anterior, tokenizamos y generamos embeddings. Esta etapa toma el Input Embedding y le hace "cositas". Los va a "normalizar". Acá creo que podemos abstraernos fuertemente y decir que esta etapa nos ayuda a brindarle estabilidad al modelo, porque es bastante probabilístico lo que hace. Está fuertemente vinculado al álgebra detrás de estos modelos, lo hablaremos en un post aparte y más técnico. Al igual que la etapa de "projection" que fue sacada, esta etapa no es necesario entenderla, y la dejo sólo para mencionar esto de que existe pero no la hablaremos.

### Self Attention

Esta parte es donde se trata de identificar que relación hay entre cada palabra, por ello es un cálculo de cuánto afecta la representación de un embedding contra todos los otros embeddings.

Vamos a tomar el ejemplo de Santiago Fiorino:

"Mañana tengo que ir al **banco** a sacar plata."

"Nos sentamos en el **banco** de la plaza a tomar mate."

![Comparativa de embeddings de las dos frases mencionadas](/assets/img/ejemplo_santiago.png)

Encima de cada palabra está su respectivo embedding, notar como la palabra **banco** tiene el mismo embedding pero se usa en frases con contextos distintos, donde uno tiene relación con una entidad financiera y el otro con un asiento. Para poder entender dicha situación, el humano interpreta el contexto donde está hubicada la palabra.
Para ello se tiene en cuenta cuánto debería afectar cada palabra a cada otra palabra, por ejemplo la relación entre banco y plata debería ser mucho más significante que la relación entre banco y mañana.

Para ello generamos una matriz NxN, donde en cada posición de la matriz estará en un valor numérico la respuesta a cuánto debería influir la palabra "i" a la hora de actualizar la palabra "j".
Textual de Santiago Fiorino.


Para cada token se utilizan tres vectores clave: Query (Q), Key (K) y Value (V).

Matriz de Query: representa lo que estamos buscando en los otros tokens
Matriz de Key: representa la "clave", qué tan inportante es un token para el otro token que estamos analizando.

Con las anteriores matrices sabemos cuánto tiene que afectar una palabra a otra pero no "como", por ello viene esta tercer matriz.

Matriz de Value: información real.

Esto tiene una fórmula terrorífica que es:

$$Attention(Q,K,V)=softmax(\frac{QK^T}{\sqrt{d_k}})V$$


![Pasos](/assets/img/pasos.png)

## Referencias

[Introducción a la IA Generativa](https://postfuturear.substack.com/p/gen-ia-lidad-3-una-introduccion-a)
[Generative AI exists because of the transformer](https://ig.ft.com/generative-ai/)
[LLM Course](https://huggingface.co/learn/llm-course/chapter1/6)
[LLM Visualization](https://bbycroft.net/llm)
[Understanding Tokenization: Breaking Down Language for AI systems](https://www.anyoneai.com/blog/understanding-tokenization-breaking-down-language-for-ai-systems)
[How are Large Language Models trained? A step-by-step guide to LLM training](https://www.anyoneai.com/blog/how-are-large-language-models-trained-a-step-by-step-guide-to-llm-training)
[Interactive Variational Autoencoder](https://robz.github.io/mnist-vae/)
[Deep Learning](https://en.wikipedia.org/wiki/Deep_learning)
[Weak artificial intelligence](https://en.wikipedia.org/wiki/Weak_artificial_intelligence)
[Tokenizer OpenAI](https://platform.openai.com/tokenizer)
[Curso de LLMs de Hugging Face](https://huggingface.co/learn/llm-course/es/chapter2/4)
[Improving Language Understanding by Generative Pre-Training](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf)
[GPT](https://huggingface.co/docs/transformers/model_doc/openai-gpt)
[BERT](https://huggingface.co/docs/transformers/model_doc/bert)
[Attention Is All You Need](arxiv.org/pdf/1706.03762)

