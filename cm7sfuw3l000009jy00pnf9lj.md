---
title: "¿Qué es el MEV?"
datePublished: Fri Mar 24 2023 03:59:21 GMT+0000 (Coordinated Universal Time)
cuid: cm7sfuw3l000009jy00pnf9lj
slug: que-es-el-mev
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679626829765/6f243321-daf3-4fdc-910d-105a5c378aa6.jpeg
tags: blockchain, defi, mev

---

## Introducción a MEV

Desde que conocí el ecosistema de Ethereum, alguien me habló de MEV y desde entonces me ha parecido un tema fascinante a la vez que misterioso y hoy con este artículo quiero empezar a diseccionarlo para entenderlo mejor.

*MEV* hace referencia a una ganancia o valor que puede ser obtenido por mineros o validadores por incluir, excluir o reordenar ciertas transacciones en determinado bloque.

*MEV* originalmente significaba *'Miner Extractable Value'* pero se cambió a *'Maximal Extractable Value'* para mantener las siglas incluso cuando Ethereum cambió a *Proof-of-Stake* y ya no hay mineros sino validadores, ya que las técnicas para extraer MEV siguen siendo en esencia las mismas.

La teoría dice que en el *MEV* las ganancias son para los mineros y validadores, pero en la práctica una buena parte del MEV es extraído por otros jugadores en el espacio llamados *'searchers'* o 'buscadores'. Los *searchers* corren *scripts* sobre los datos que arroja la blockchain para detectar oportunidades de hacer algo de dinero y regularmente tienen bots que envían las transacciones adecuadas a la red.

Los mineros/validadores de cualquier manera se benefician de este proceso, pues una vez que los *searchers* detectan una oportunidad de ganar, compiten porque su transacción sea la primera en ser incluida, y están dispuestos a pagar un *gas fee* más alto que sus competidores para lograrlo. Por supuesto, asumimos que un *searcher* se porta de manera economicamente racional, y no va a pagar más *gas fee* que la ganancia potencial de su transacción.

Dicho esto, algunas oportunidades de extraer MEV son muy competidas, como hacer arbitraje sencillo en un DEX, por lo que se ha visto a searchers pagar hasta el 90% o más de su posible ganancia de MEV para garantizar que su transacción sea procesada.

### Gas Golfing

*Gas golfing* es la actividad de buscar técnicas para ahorrar la mayor cantidad de gas. Por ejemplo, si soy un searcher y (usaré números al azar) mi transacción de arbitraje gasta 30000 gas y pongo mi precio de gas en 10, gastaré 300,000 unidades en gas fees, pero si logro bajar lo que gasta mi transacción a 15000 gas, ahora puedo ofrecer pagar hasta 20 de *gas price* y el total que gastaré seguirá siendo 300,000 unidades.

Un par de técnicas de gas golfing como ejemplo:

* Usar direcciones que tengan muchos 0s al comienzo: E.j: [0x0000000000C521824EaFf97Eac7B73B084ef9306](https://etherscan.io/address/0x0000000000c521824eaff97eac7b73b084ef9306) ya que requieren menos espacio (y gas por ende) para almacenarse.
    
* Dejar pequeñas cantidades de tokens en los contratos, ya que cuesta más gas inicializar un espacio de almacenaje (el caso si el balance fuera 0) que actualizar el mismo espacio de almacenaje.
    

### Frontrunners generalizados

No todos los searchers ejecutan algoritmos complicados para encontrar oportunidades de MEV. Los *frontrunners generalizados* son bots que vigilan la *mempool* para detectar transacciones rentables. Si encuentran una, simplemente copian los datos de la transacción, la ejecutan localmente para asegurarse de que sigue siendo rentable, y luego reemplazan la dirección original con la dirección del searcher, ofrecen un gas price más alto y la envían, basicamente esto es lo que se llama hacer *frontrunning*.

### Flashbots

[Flashbots](https://github.com/flashbots/pm) es un proyecto independiente basado en el cliente geth que permite a los searchers enviar sus transacciones a los mineros sin revelarlas a la mempool pública.

## Tipos de MEV

### Arbitraje en DEXes

Esta es la forma más simple, conocida y competida de MEV. Consiste en lo siguiente:

Si dos DEXes ofrecen un token cada uno con diferente precio, cualquiera puede comprar el token más barato en el DEX 1 y venderlo más caro en el DEX 2 en una única transacción atómica. Este tipo de arbitraje sin riesgo es posible gracias a la blockchain.

La documentación de Ethereum provee [este ejemplo](https://etherscan.io/tx/0x5e1657ef0e9be9bc72efefe59a2528d0d730d478cfc9e6cdd09af9f997bb3ef4) donde un searcher convirtió 1000 ETH en 1045 ETH aprovechando los cambios de precio en el par ETH/DAI en Uniswap vs Sushiswap.

### Liquidaciones

Las liquidaciones en procolos de préstamos son otra oportunidad de MEV muy conocida, funcionan así:

Un protocolo de préstamos como Aave o Maker ofrece préstamos de diferentes tokens y activos. Para acceder a ellos, los usuarios deben dejar otra criptomoneda como colateral (generalmente ETH).

Por ejemplo, si yo quiero que me presten $1000 del *token de gobernanza* MKR debo dejar $1500 de ETH como garantía o *'colateral'* (las tasas exactan cambian según varios factores). Pero qué sucede si digamos, el precio de ETH comienza a caer abruptamente? Si mi garantía deja de tener el valor que tenía, el protocolo permite que se me liquide, devolviéndole su dinero a mis prestamistas, y después pagando una cuota al liquidador o *liquidation fee*.

Y aquí es donde está la oportunidad de MEV. Los searchers *parsean* la data disponible tan rápido como pueden para detectar donde hay una oportunidad de liquidación y ser los primeros en mandar la transacción y quedarse con la quota de liquidación.

### Sandwich Trading

Funciona de la siguiente manera:

Un searcher vigila la mempool en busca de trades muy grandes en DEXes. Por ej. alguien que quiera comprar 10000 UNI con DAI en Uniswap. Por la manera en la que funciona un DEX, este trade va a ocasionar que el precio del UNI comparado con DAI se eleve bastante momentaneamente después de la operación.

Lo que hará entonces el searcher es ejecutar una orden de compra de UNI justo antes del trade enorme en cuestión, y luego una orden de venta inmediatamente después del mismo trade, de ahí el nombre de sandwich.

Sin embargo, esta operación no es atómica lo que la convierte en algo más riesgoso y susceptible a algo llamado [ataque de salmonella](https://github.com/Defi-Cartel/salmonella). (Cárteles DeFi, ataques sandwich, contraataques salmonella donde se juegan cientos de miles de dólares y la estabilidad del ecosistema cripto, ¿a alguien le podrá parecer esto aburrido? 🤔)

### NFT MEV

El MEV en el espacio de los NFTs es un fenómeno más nuevo y poco explorado, pero como las transacciones de NFTs suceden en la misma blockchain de Ethereum, están sujetas a técnicas similares a las que hemos hablado, ejemplo:

Hay un drop de una colección de NFTs muy sonada. Un searcher puede programar una transacción para ponerse primero en la lista para comprar el NFT o NFTs. O si alguien enlista un NFT con un precio ridiculamente bajo por error, el searcher puede hacer frontrun a otros compradores y quedarse con la oportunidad, [como en esta historia](https://www.theblock.co/post/113546/mistake-sees-69000-cryptopunk-sold-for-less-than-a-cent). ¿Te das cuenta? Podríamos compararlo con un robo de una pieza de arte 🎨!

### Pero hay más

Todo esto de lo que hablé, arbitraje en DEXes, liquidaciones, y sandwich trading son oportunidades de MEV demasiado conocidas y competidas, por lo que pueden ser demasiado difíciles de implementar para searchers que van llegando al espacio. Sin embargo, el ecosistema cambia todos los días y surjen y mueren todo tipo de oportunidades de explorar e investigar sobre este apasionante tema.

La documentación de Ethereum provee [este link](https://github.com/flashbots/mev-job-board) con oportunidades de MEV.

## Efectos del MEV

MEV es un factor del ecosistema blockchain que tiene el potencial de ponerlo en serio riesgo, así como también de encausarse como un incentivo más para que los actores involucrados en él sigan participando de una forma neta positiva.

### Lo bueno

Muchos proyectos de DeFi dependen de que existan actores economicamente racionales para garantizar la estabilidad de los protocolos. Sin actores economicamente racionales buscando oportunidades que a la vez arreglan pequeñas ineficiencias económicas, estas dapps no serían tan robustas como lo son hoy en día.

### Lo malo

En la *capa de aplicación*, técnicas como el *sandwich trading* dan como resultado una mala experiencia para los usuarios que mandaron la transacción original, pues terminan perdiendo dinero.

En la *capa de red*, los frontrunners generalizados y las PGAs (price-gas auction) provocan la congestión de la red y precios de gas altos para todas las personas tratando de usar la red para sus actividades regulares.

Más allá de lo que pasa en cada uno de estos bloques, es preocupante lo que puede llegar a pasar entre varios bloques, ya que si una oportunidad de MEV resulta significativamente más jugosa que los fees que cobra el validador, éste puede verse incentivado a reorganizar los últimos bloques y capturar el MEV por su cuenta, causando que se reorganice la blockchain y se ponga en peligro el consenso de la red, y en última instancia la integridad de toda la blockchain.

## A manera de conclusión

El tema de MEV tuvo su pico en 2021, cuando los primeros searchers que descubrieron estas oportunidades congestionaron la red de una manera significativa. Desde entonces, la organización Flashbots ha ayudado a gestionar la manera en la que se extrae este MEV para que resulte menos dañino para otros usuarios.

Aunque todavía hay quien se aprovecha de jugosas oportunidades en MEV, la competencia y la dificultad han provocado que searchers se muevan a buscar oportunidades en otras blockchains menos competidas como Binance Smart Chain.

Por otro lado, todavía queda por ver cómo cambiará el panorama MEV conforme Ethereum siga evolucionando hacia usar *shards* y más de la actividad se mueva a soluciones *layer 2*.

Si sientes que ya habías leído estas explicaciones es porque están tomadas de la documentación de [Ethereum en inglés](https://ethereum.org/en/developers/docs/mev/), en la cual me basé para crear este primer artículo de varios más que estaré escribiendo sobre MEV, todo con el afán de explicar y entender mejor estos interesantes pero complicados temas.  
  
[Artículo publicado originalmente](https://garosan.hashnode.dev/que-es-el-mev) en garosan.xyz.