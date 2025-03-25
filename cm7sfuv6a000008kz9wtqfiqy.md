---
title: "Introducción a las Layer 2s"
datePublished: Sun Dec 03 2023 06:10:37 GMT+0000 (Coordinated Universal Time)
cuid: cm7sfuv6a000008kz9wtqfiqy
slug: introduccion-a-las-layer-2s
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701563097265/2ecb7307-abb5-4b4a-aab3-11b4a9f959cb.png
tags: blockchain, layer2

---

Si te has adentrado un poco en el ecosistema de Ethereum, seguramente has escuchado estos términos en algún momento: Layer 2, optimistic, zK, rollups, pero ¿qué es todo esto? Aquí lo trataré de explicar de la manera más sencilla.

## ¿Qué son Layer 2s?

Layer 2 (L2) es el término que usamos para describir un grupo específico de tecnologías que buscan resolver el problema de escalabilidad de Ethereum.

En este contexto, la Layer 1 sería la blockchain principal, como Ethereum o Bitcoin, y ejemplos de Layer 2s serían los 'rollups' en Ethereum y la Lightning Network en Bitcoin.

Las Layer 2 de Ethereum, se apoyan en las capacidades de la Layer 1 para proveer datos y la seguridad de que las transacciones son correctas, pero esto lo veremos más adelante.

## ¿Por qué necesitamos blockchains Layer 2?

El *blockchain trilemma* nos dice que una arquitectura de blockchain regular solamente puede lograr 2 de las siguientes 3: descentralización, seguridad, y escalabilidad. El objetivo principal de una L2 es aumentar el rendimiento transaccional (la cantidad de transacciones por segundo que se pueden procesar) sin sacrificar la descentralización o la seguridad.

La *mainnet* de Ethereum (L1) solo puede procesar 15 transacciones por segundo en promedio. Cuando la demanda es alta, la red se congestiona y las comisiones de la red aumentan. Las Layer 2s son soluciones para reducir esas comisiones al procesar las transacciones fuera de la red principal (off-chain).

Entonces podemos decir que algunos beneficios de las Layer 2 son:

* Comisiones de red más bajas
    
* Mantener la seguridad como en la Layer 1
    
* Más casos de uso al ser una red más eficiente
    

Ya que tenemos una idea general de que es una Layer 2 y qué problema está tratando de resolver, surge inevitablemente la pregunta.

## ¿Cómo funciona una Layer 2?

Una Layer 2 es una blockchain en sí misma que extiende las capacidades de Ethereum (u otra blockchain L1). Hay diferentes tipos de L2s, y cada una tiene su propia arquitectura y modelo de seguridad, las principales son:

### Rollups 🌯

Los rollups agrupan o *enrollan* cientos de transacciones en una sola transacción en la L1. De esta manera, las comisiones de postear la transacción en la L1 son divididas entre todos los que participaron. Las transacciones de un rollup son ejecutadas fuera de la L1, pero los datos de transacciones son enviados a Ethereum. Una vez que la transacción rollup es aceptada, se necesitaría revertir la blockchain de Ethereum para revertir la transacción rollup, lo que la hace bastante segura.

Hay 2 tipos de rollups: optimistic y ZK (zero-knowledge), y la principal diferencia está en cómo envían la data de transacciones a la L1:

**Optimistic rollups:** Se asume que las transacciones son válidas al llegar a la L1, pero pueden ser disputadas de ser necesario. Si se sospecha de una transacción inválida, se ejecuta una prueba de falla (fault proof) para confirmar la sospecha. [Más Info](https://ethereum.org/es/developers/docs/scaling/optimistic-rollups/).

Zero-knowledge rollups: Usan pruebas de validez para las transacciones que son procesadas off-chain, y luego comprimen cierta data para enviarla a Ethereum o la L1 como prueba de validez. [Más Info](https://ethereum.org/es/developers/docs/scaling/zk-rollups/).

### Riesgos

Es importante anotar que muchos proyectos L2 son todavía muy jóvenes y requieren que los usuarios confíen en que los operadores actuarán honestamente, mientras el proyecto aún no está lo suficientemente descentralizado. Un excelente recurso para consultar el estado de las L2s es [L2Beat](https://l2beat.com/scaling/risk).

## Tipos de Layer 2s

Ahora veamos algunos tipos de Layers 2 que menciona la documentación oficial de Ethereum:

### Layer 2s generalizadas

Una layer 2 generalizada es basicamente como Ethereum, pero más barata. Todo lo que puedes hacer en una L1, lo puedes hacer en una L2 de estas, algunos ejemplos son:

* [Arbitrum](https://arbitrum.io/)
    
* [Optimism](https://www.optimism.io/)
    
* [Boba Network](https://boba.network/)
    
* [Starknet](https://www.starknet.io/en)
    

### Layer 2s de aplicación específica

Algunas layer 2s nacen con el propósito específico de resolver un problema particular, algunos ejemplos son:

* [Loopring](https://loopring.org/#/)
    
* [zkSync](https://zksync.io/)
    
* [ZKSpace](https://zks.org/)
    
* [Aztec](https://aztec.network/)
    

### Sidechains, Validiums y otras blockchains

Las sidechains y validiums son blockchains que corren en paralelo a Ethereum, e interactúan con éste através de puentes, pero no obtienen su seguridad ni disponibilidad de datos de Ethereum. Ambas soluciones tienen la misma finalidad que las L2s pero tienen un funcionamiento y arquitectura fundamentalmente diferentes.

[Más sobre sidechains](https://ethereum.org/en/developers/docs/scaling/sidechains/)

[Más sobre validiums](https://ethereum.org/en/developers/docs/scaling/validium/)

Finalmente, hay más blockchains L1 que reportan tener mayores transacciones por segundo y comisiones más bajas que Ethereum, pero de manera general presentan fallas, problemas de seguridad o simplemente no son descentralizadas.

Esta fue una pequeña introducción al concepto de Layer 2s tomando como base la documentación de Ethereum, en los próximos días seguiré investigando sobre estos temas y en particular sobre Arbitrum, la L2 con mayor market share del ecosistema (53%) y un valor total bloqueado de $7.96B USD! Sigamos explorando las fronteras! 👨‍🚀🛰️  
  
[Artículo publicado originalmente](https://garosan.hashnode.dev/introduccion-a-las-layer-2s) en garosan.xyz.