---
title: "Introducción a Arbitrum, una de las mejores L2s ahí afuera"
datePublished: Wed Oct 02 2024 02:51:24 GMT+0000 (Coordinated Universal Time)
cuid: cm7sfupwp000009jv29fb2abq
slug: introduccion-a-arbitrum-una-de-las-mejores-l2s-ahi-afuera
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729279745934/c6a4fd0a-4530-4f64-9efe-1e61f0220a78.png
tags: web3, layer2, arbitrum

---

Hola, hoy quiero hacer un artículo sobre Arbitrum, esa L2 que vemos por todas partes, en todas las conferencias y eventos cripto, y que de acuerdo a [L2Beat](https://l2beat.com/scaling/summary), es la Layer 2 número 1 por TVL. Además tiene una comunidad vibrante y una buena cantidad de oportunidades de crecer así que vamos a meternos a la documentación, y entender los conceptos básicos juntos.

Empecemos con la pregunta más básica.

## ¿Qué es Arbitrum? 🚀

Arbitrum es un conjunto de tecnologías creadas para escalar Ethereum. Puedes usar las cadenas de Arbitrum para hacer todo lo que se puede hacer en Ethereum, pero más rápido y más barato, ¿genial no? El producto bandera de Arbitrum se llama **Arbitrum Rollup**, y es un rollup optimista que hereda su seguridad de Ethereum.

## ¿Pero porqué necesitamos Arbitrum? 🤔

Pues resulta que Ethereum, a pesar de lo cool que es, está bastante limitado. Solo permite hacer de 20 a 40 transacciones por segundo (TPS), y cuando se congestiona, las personas compiten por incluir sus transacciones lo que eleva el costo de las comisiones.

Ahora dirás, ¿por qué Ethereum es tan limitado? Pensé que Vitalik era un genio 😓. Pues sigue leyendo para que lo sigas pensando 🤓…

Ethereum es lento y limitado por diseño. Para mantener la descentralización y la accesibilidad, todos los nodos de Ethereum deben procesar cada transacción realizada en la red desde su creación. Esto garantiza que cualquiera pueda ejecutar un nodo de Ethereum sin necesitar equipos costosos. Sin embargo, esta característica también limita el número de transacciones que se pueden procesar.

## ¿Cómo soluciona el problema Arbitrum Rollup?

Esta es la idea básica: La cadena Arbitrum Rollup corre como un submódulo dentro de Ethereum. Ethereum no necesita verificar todas las transacciones de Arbitrum; en lugar de eso, Ethereum asume *optimistamente* que las transacciones que vienen de Arbitrum están siguiendo las reglas. Si ocurre una violación, la transacción sospechosa puede ser disputada en la L1. Si se comprueba la violación, la transacción es deshechada y el actor malicioso será penalizado financieramente. Mientras podamos confiar en la seguridad de Ethereum, cualquier persona interesada puede ver las transacciones y detectar y probar fraudes.

## Ok ¿Pero quién en realidad está checando transacciones buscando fraudes? 👮

Estas personas se llaman *validadores*. Arbitrum no espera que todos sus usuarios estén interesados en correr el software validador, pero la parte crucial es ¡que cualquiera puede hacerlo si quiere! Pronto cualquier persona podrá ser un validador de Arbitrum, pero por lo pronto hay una [lista de entidades permitidas](https://docs.arbitrum.foundation/state-of-progressive-decentralization) y el software es open source.

## **¿Cómo se prueba el fraude en Arbitrum?** 🧐

Para probar un fraude, los validadores de Arbitrum (quienes actualizan el estado de la cadena en la L1) juegan un *juego de disputa* interactivo. En este juego, dos validadores que no están de acuerdo limitan su disputa a un único paso computacional (como multiplicar dos números), que luego es ejecutado en la L1 de Ethereum para determinar quién tiene la razón. Este proceso garantiza que siempre se identifique al validador honesto.

## **¿Este proceso de disputa genera algún retraso para los usuarios de Arbitrum?** ⌛

La única demora que un usuario puede experimentar es al retirar fondos de Arbitrum a Ethereum, lo cual típicamente tarda una semana. Sin embargo, los usuarios pueden evitar esta espera usando aplicaciones de *puente-rápido*, que permiten retirar fondos más rápido a cambio de una pequeña comisión. Cualquier otra acción, como depositar fondos desde Ethereum en Arbitrum o usar aplicaciones descentralizadas (dapps) en Arbitrum, no sufre esta demora.

## **Entonces ¿Cómo Arbitrum ofrece tarifas más bajas?** 🤑

La ejecución optimista es la base de los ahorros en las fees, pero Arbitrum también reduce la carga en la L1 de otras formas. Las transacciones de Arbitrum se envían a la L1 en lotes, lo que permite agrupar muchas transacciones en una sola. Esto reduce significativamente el costo por transacción. Además, los datos de las transacciones se publican en la L1 de manera comprimida y solo se descomprimen dentro del entorno de la L2, lo que minimiza aún más su impacto en la L1.

## **Una vez más ¿La experiencia de usar Arbitrum es parecida a la de Ethereum?**

Arbitrum prioriza la compatibilidad con Ethereum, lo que significa que los usuarios pueden interactuar con Arbitrum usando sus carteras favoritas de Ethereum y los desarrolladores pueden desplegar contratos con las mismas herramientas que usan en Ethereum. En la mayoría de los casos, usar Arbitrum se siente igual que usar Ethereum, con la gran diferencia de que es más rápido y económico.

Para lograr esta compatibilidad, Arbitrum utiliza una versión modificada de Geth (la implementación de Ethereum más usada), lo que lo convierte en una L2 de confianza.

## **¿Y qué es una AnyTrust Chain?** ⛓️

Una cadena AnyTrust de Arbitrum no tiene las mismas garantías de seguridad descentralizada que una Rollup, lo que permite reducir aún más los costos de transacción. En una cadena AnyTrust, los datos se gestionan fuera de la L1, y en caso de una disputa, la cadena vuelve al modo rollup para resolverla. Esto la hace ideal para aplicaciones que necesitan un alto rendimiento de transacciones sin requerir la descentralización completa.

## \*\*Recapitulando…\*\*🤓

Ha sido un artículo bastante denso (y bastante basado en los docs oficiales 😉) así que vamos a tratar de recapitular lo principal de Arbitrum que aprendimos hoy:

* 👉 Arbitrum es un conjunto de soluciones L2 que nos permiten transacciones mucho más rápidas y baratas que Ethereum.
    
* 👉 Arbitrum hereda su seguridad de Ethereum: Mientras podamos confiar en Ethereum, podemos confiar en Ethereum.
    
* 👉 Un validador es una entidad que valida que las transacciones de Arbitrum no sean fraudulentas.
    
* 👉 Lo único que toma más tiempo de lo normal es retirar nuestros fondos de Arbitrum a Ethereum pero podemos usar un puente rápido como solución.
    
* 👉 Actualmente hay 2 cadenas de Arbitrum desplegadas en Ethereum: Una del tipo Rollup llamada **Arbitrum One**, y una del tipo AnyTrust llamada **Arbitrum Nova**. Cada usuari@ o developer decide cual es mejor para su caso de uso.
    

Espero que te haya gustado este artículo y poder seguir compartiendo más de este apasionante ecosistema. Pronto estaré subiendo más material sobre desarrollar en Arbitrum así que mantente al pendiente, y déjame saber si te sirvió de algo este contenido escrito, LFG! 🚀

[Artículo publicado originalmente](https://garosan.hashnode.dev/introduccion-a-arbitrum-una-de-las-mejores-l2s-ahi-afuera) en garosan.xyz.