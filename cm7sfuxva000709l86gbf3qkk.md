---
title: "El ecosistema DeFi y sus capas"
datePublished: Tue Mar 07 2023 14:53:08 GMT+0000 (Coordinated Universal Time)
cuid: cm7sfuxva000709l86gbf3qkk
slug: el-ecosistema-defi-y-sus-capas
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678161235863/768fca0d-67ff-4b78-ac8a-fbb80a78f974.jpeg
tags: blockchain, defi

---


En este artículo (tomando como base [este curso](https://www.unic.ac.cy/blockchain/free-defi-mooc/)), hablo de las diferentes capas que componen el ecosistema DeFi (settlement, activos, protocolo, aplicación y agregación), así como de sus tokens, standards, y la composibilidad, esa característica que hace que DeFi sea conocido como 'money legos'.

# Las capas del stack DeFi

![Foto tomada del curso de DeFi de la Universidad de Nicosia](https://cdn.hashnode.com/res/hashnode/image/upload/v1678161506954/afc4f958-cba7-4cf4-ad45-9c00cb280829.png align="center")

Esta imagen representa las diferentes capas que de manera general constituyen un ecosistema DeFi dentro de una blockchain. Por supuesto, es sólo un modelo útil para explicar las cosas y constantemente surgen nuevos protocolos y aplicaciones que desafían estas barreras. Revisemos capa por capa.

## La capa de settlement o acuerdo

El verbo *to settle* aquí significa liquidar, finalizar o *llegar a un acuerdo* sobre algo, así que esta primera capa es donde se finalizan todas las transacciones que suceden en el ecosistema. En el caso de Ethereum, la capa incluye la red en sí, al igual que su token nativo 'Ether'.

Esta capa tiene 3 funciones principales:

* Guardar información relevante como el estado de transacciones, quién es dueñ@ de qué, de manera segura.
    
* Asegurarse que los cambios de estado (cambios de balance, cambios de posesión de los activos) sigan las reglas de la blockchain.
    
* Permitir la ejecución automática y decentralizada de los *smart contracts* que componen los protocolos.
    

Como las blockchains son la primera capa, normalmente se les conoce como Capa 1 o Layer 1. Algunas de las principales son Ethereum, Avalance, Binance Smart Chain, Solana, Cardano, etc.

## La capa de activos

La capa de activos o *asset layer* es la que tiene qué ver con todos los activos o tokens que son emitidos dentro de la red.

Cada blockchain tiene sus propias reglas para los tokens que se pueden emitir. En el caso de Ethereum estas reglas se llaman ERCs o *Ethereum Request for Comment* y funcionan así: Normalmente uno de los desarrolladores que están manteniendo el código de la blockchain dice '*Hey, tengo una idea de algo que podriamos implementar'*, entonces crea un ERC y lo somete a la opinión de los demás desarrolladores de la red. En Ethereum, el ERC-20 es el standard que define los tokens fungibles, el ERC-721 define los NFTs, etc. En la blockchain de Solana estos estándares se llaman SLP (*Solana Program Library*), en el caso de Binance Smart Chain se llaman BEP o *Binance Chain Evolution Proposal*, etc.

### ¿Para qué sirven todos estos tokens?

Y ¿para qué querría yo un token de esa cosa llamada Uniswap? te podrás estar preguntando, y bueno, va más o menos de la siguiente manera:

* El token nativo de la blockchain, llámese ETH para Ethereum, SOL para Solana, AVAX para Avalanche, etc., es el que necesitamos para poder hacer transacciones en la blockchain. ¿Quieres comprar un NFT de changuitos? Claro que sí, sería 0.002 ETH de *transaction fee*, ¿quieres comprar un token dentro de Avalanche que te permitirá participar en el juego más cool que has visto? 0.03 AVAX, pase a la caja. Para esto es que necesitamos los tokens nativos.
    
* Los tokens no nativos en cambio, nos permiten hacer basicamente lo que sea que los creadores del protocolo hayan decidido que se puede hacer con su token, en el ecosistema de DeFi que es nuestro tema, los tokens generalmente cumplen dos propósitos principales:
    
    * **Tokens de gobernanza (Governance token)**: Permiten a sus dueñ@s votar sobre propuestas que afectan directamente al protocolo en cuestión, como derechos de voto de un accionista.
        
    * **Tokens de proveedor de liquidez (LP token)**: Es un token que te dan como 'recibo' de que depositaste tus activos en un pool de liquidez DeFi (Nos sumergiremos en el tema más adelante 😄).
        

¿Puedes reconocer a qué proyectos pertenecen los siguientes tokens? ¡Te lo dejo de tarea!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678167189715/68643e54-929a-482a-bfea-2afd8b959939.png align="center")

## Capa de protocolo

La capa de protocolo se refiere a los *smart contracts* que son los que hacen funcionar todas las dapps. Luego, los desarrolladores crean interfaces (capa de aplicación) que nos permiten a todos los usuarios interactuar con estos smart contracts o protocolos. Por la naturaleza de la blockchain, incluso si alguien hackeara la interfaz o un gobierno ordenara dar de baja la interfaz de un protocolo blockchain, cualquier persona podría crear otra interfaz para interactuar con el protocolo, ya que éste vive en la blockchain, y una blockchain lo bastante descentralizada es practicamente imposible de detener.

Por poner un ejemplo, [https://uniswap.org/](https://uniswap.org/) es la interfaz (o frontend) de Uniswap, y fue creada por Uniswap Labs, la compañía que se constituyó legalmente para poder acatar las normas del gobierno de Estados Unidos. La misma Uniswap Labs creó los [contratos inteligentes](https://github.com/Uniswap/v3-core/tree/main/contracts) (backend) que hacen funcionar a Uniswap, pero éstos ahora viven en la blockchain, para pararlos, tendrías qué detener toda la red de Ethereum 🤔.

## Capa de aplicación

Ésta es la capa que permite a los usuarios interactuar con los protocolos. Como te expliqué en el punto anterior, consiste en las interfaces o frontends a las que les haces click aquí y allá para poder intercambiar tus tokens, prestar o pedir prestado, o generar ingresos pasivos en aplicaciones blockchain.

Algunos ejemplos de dapps que te permiten intercambiar tokens y mucho más son [Uniswap](https://uniswap.org/) en Ethereum, [TraderJoe](https://traderjoexyz.com/avalanche) en Avalanche y [PancakeSwap](https://pancakeswap.finance/) en Binance Smart Chain. (Una nota de seguridad, **siempre fíjate muy bien en la barra de direcciones de tu navegador, pues no faltarán agentes maliciosos que te dirijirán a *uniiswap.org* en lugar de uniswap.org** **o páginas similares que se verán muy parecidas a la original**, siempre con la intención de robarse tus tokens, ¡cuidado!).

## Capa de agregación

La capa de agregación o aggregation layer es una extensión de la capa de aplicación, o en otras palabras, son servicios que combinan la información y las funcionalidades de varias aplicaciones en una sola.

Algunas de las aplicaciones más populares son servicios que te permiten ver todos los activos que tienes en diferentes blockchains en un solo lugar como Zapper, o servicios que te ayudan a buscar el precio más conveniente en todos los *exchanges* disponibles cuando quieres tradear algún token, como 1inch.

## Componibilidad en DeFi

La componibilidad, conocida como composability en inglés, es la característica de los protocolos de DeFi de poder interactuar unos con otros de manera independiente, sin requerir permisos. Esto crea un gran incentivo para innovar y formar nuevos complejos servicios financieros que de otra manera no serían posibles.

En el mundo web2, cada servicio está cerrado y celosamente controlado. Twitter, Facebook, y Linkedin por ejemplo no suelen permitirte crear integraciones muy sofisticadas entre ellos. Por ejemplo, si yo como desarrollador quisiera crear un servicio que integre todos los datos de estas redes sociales en una interfaz que yo maneje, seguramente sería bloqueado por estas compañías ya que esta idea mía no les conviene en absoluto.

En DeFi es diferente, los contratos inteligentes que son el corazón y cerebro de los protocolos están ahí, libres en la blockchain, y cualquiera puede interactuar con ellos. Esto ha permitido la explosión del ecosistema y la creación de servicios cada vez más complejos en su funcionamiento interior, pero que permiten al usuario acceder a ellos por una interfaz cada vez más amigable.
