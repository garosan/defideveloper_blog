---
title: "Hola Mundo, Hola Solidity!"
datePublished: Sat Dec 07 2024 02:39:52 GMT+0000 (Coordinated Universal Time)
cuid: cm7sob81w000509jsa0et6m8h
slug: hola-mundo-tu-primer-smart-contract-en-remix
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733540143003/59dcc9ed-a2c6-43a3-af46-ea8f9bc9b4e6.png

---


Al explorar el desarrollo en blockchain, uno de los primeros pasos es familiarizarte con **Remix**, un entorno de desarrollo en nuestro navegador diseñado específicamente para crear y probar contratos inteligentes en **Solidity**. Es sencillo de usar y no requiere instalación, lo que lo hace perfecto para que hagamos nuestras primeras pruebas sin preocuparnos por instalar nada en nuestra computadora.

## ¿Qué es Remix?

[Remix](https://remix.ethereum.org) es una herramienta que nos permite **escribir, compilar, y desplegar** smart contracts directamente desde nuestro navegador. Tiene un editor de código integrado y herramientas como un compilador, una consola y un simulador de una blockchain virtual que nos permitirá aprender muchísimo sin siquiera tener qué conectar nuestra wallet. ¡Un entorno perfecto para nosotros que estamos comenzando!

---

## Primeros Pasos con Remix: Escribiendo tu Primer Contrato

¡Pongamos manos a la obra! Y como dictan las buenas costumbres, crearemos un contrato llamado `Hello World`, este contrato contendrá dos funciones que retornan datos básicos.

### Paso 1: Crea un nuevo archivo `.sol`

1. Ve a [remix.ethereum.org](https://remix.ethereum.org). Es muy importante que te asegures que estás en la dirección correcta. ¡Ten cuidado con estafas!
    
2. En el panel lateral izquierdo, haz clic en **File Explorer** y crea un archivo nuevo llamado `HelloWorld.sol`. La extensión `.sol` indica que es un archivo de Solidity.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733925956465/8f55dc1c-55dc-4025-a926-2c6afa0e74c2.png align="center")

### Paso 2: Escribe el Contrato

Copia y pega el siguiente código dentro del archivo `HelloWorld.sol`:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract HelloWorld {
    function helloWorld() public pure returns (uint256) {
        return 100;
    }

    function returnsBool() public pure returns (bool) {
        return true;
    }
}
```

Verás una advertencia de que tengas cuidado con el código que pegues. Puedes leerla y aceptarla.

Este contrato define dos funciones simples:

* `helloWorld()`: Retorna el número `100`.
    
* `returnsBool()`: Retorna el valor booleano `true`.
    

---

## Compilando tu Contrato

### Paso 1: Seleccionar el Compilador

1. En el panel izquierdo de Remix, haz clic en la pestaña **Solidity Compiler**.
    
2. Asegúrate de que la versión del compilador coincida con la versión declarada en el contrato (`pragma solidity ^0.8.0;`), Normalmente Remix se encarga de esto en automático, pero para que sepas cualquier versión del compilador que empiece con `0.8.x` funcionará.
    
3. Haz clic en **Compile HelloWorld.sol**.
    

Si todo está correcto, deberías ver un checkmark verde en el ícono del compilador.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733538521140/bb14fcbf-9a98-4d9b-99b0-aa1549165d80.png align="center")

---

## Desplegando el Contrato en Remix

Remix incluye una red virtual que simula el comportamiento de una blockchain real. Así puedes desplegar y probar tu contrato sin necesidad de usar dinero real, conectar tu wallet o buscar fondos de testnet en un faucet (si no entiendes estos términos, no te preocupes los veremos más adelante).

### Paso 1: Acceder al Desplegador

1. Ve a la pestaña **Deploy & Run Transactions** en el panel izquierdo.
    
2. Asegúrate de que el **Environment** esté configurado en "Remix VM" (no importa que diga Cancun o London o cualquier otra versión).
    

### Paso 2: Desplegar el Contrato

1. Bajo la sección "Deploy", selecciona el contrato `HelloWorld`.
    
2. Haz clic en el botón naranja **Deploy**.
    

Una vez desplegado, verás el contrato listado bajo la sección "Deployed Contracts" y verás una palomita verde en la consola indicando que la transacción fue exitosa.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733538933651/81b7876f-a44f-4d73-b5ca-7bbd1225977a.png align="center")

---

## Probando el Contrato

1. Expande el contrato en "Deployed Contracts".
    
2. Haz clic en las funciones `helloWorld` y `returnsBool` para ejecutarlas.
    
3. Observa cómo retornan los valores `100` y `true`, respectivamente.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733539016786/09afe91f-d289-46fd-aadb-17d4f94ec577.png align="center")

---

¡Felicidades! Has dado tus primeros pasos como desarrollador/a blockchain, sigamos adelante. 🚀
