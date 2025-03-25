---
title: "Introducción a HardHat 👷"
datePublished: Sat Nov 30 2024 02:13:10 GMT+0000 (Coordinated Universal Time)
cuid: cm7sob9rc000609jsdgnae2k3
slug: introduccion-a-hardhat
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1732926613541/3863f787-bce0-4203-b8e6-4f36acfde597.webp

---


Hoy vamos a ver una pequeña introducción a Hardhat explicada de manera sencilla para principiantes. El objetivo es que después de leer este tutorial entiendas mucho mejor esta herramienta y empieces tu camino hacia construir dapps de manera profesional, ¡comencemos!

### ¿Qué es Hardhat? Componentes principales

Primero que nada, es importante saber que Hardhat es un grupo de herramientas con diferentes utilidades:

**Hardhat Runner:** Es el componente principal de Hardhat, es un *task runner* que nos ayuda con todas las tareas relacionadas al desarrollo blockchain.

**Hardhat Network:** Es un simulador de un nodo local de la red de Ethereum, nos permite emular la blockchain y hacer pruebas locales en nuestra computadora.

**Hardhat Ignition:** Es un sistema nuevo para hacer más fluido el proceso de desplegar nuestros contratos.

**Extensión de VS Code:** Hardhat creó una extensión de VS Code que es la más recomendada. Mírala en su [página oficial](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity).

**Hardhat Chai Matchers:** Chai es una librería de pruebas muy usada en el ecosistema de JavaScript. Hardhat añade funcionalidad específica de blockchain para que escribamos mejores tests de nuestros contratos.

Entonces, ya sabemos que Hardhat es un set de herramientas y la principal es su *task runner*. Un *"task runner"* es una herramienta que permite automatizar tareas repetitivas, como compilar código, ejecutar pruebas o desplegar contratos inteligentes. Todo en Hardhat gira en torno a los conceptos de tareas y plugins. Cuando compilamos o desplegamos nuestros contratos, estamos corriendo tareas. Hardhat nos permite crear nuestras propias tareas y crear flujos bastante avanzados con ellas.

### Instalando Hardhat

Ahora sí viene lo bueno, ¡vamos a programar!

Empecemos creando un nuevo folder en una carpeta donde tengas tus proyectos de código:

`mkdir hardhat-prueba   cd hardhat-prueba`

Dentro de este folder, inicializamos un proyecto de npm corriendo:

`npm init -y`

A continuación instalamos Hardhat como dependencia de desarrollo (también puedes usar yarn, pero se recomienda usar npm 7 o posterior):

`npm install --save-dev hardhat`

Nota: La documentación de Hardhat recomienda que si estamos en Windows usemos WSL pero yo hice pruebas en el sistema normal de Windows y no tuve ningún problema.

Ahora iniciemos un proyecto muestra corriendo:

`npx hardhat init`

Seleccionemos *‘Create JavaScript project’* y demos Enter en las demás preguntas. (Para poder seleccionar necesitas una terminal interactiva, si estás en Windows, GitBash no te servirá para este paso, te recomiendo usar PowerShell):

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1732929433602/93ddef9c-29d8-424e-9051-59f36bfff6d4.png align="center")

Como dijimos antes, el concepto principal en Hardhat son las tareas, así que corre `npx hardhat` y veras algunas de las tareas disponibles. Por ejemplo 3 de las tareas que vamos a usar muy seguido serán `compile`, `test` y `node`. Cuando instalemos algún plugin, éste nos hará disponibles nuevas tareas que podremos ver también en esta lista.

Nuestro flujo de trabajo será así: 1) Escribir un contrato inteligente, 2) Escribir tests para este contrato y 3) Desplegar nuestro contrato a una blockchain

### Escribiendo y compilando el smart contract

Cuando corrimos `npx hardhat init` se creó un contrato de prueba en `contracts/Lock.sol`. Te recomiendo que leas con detenimiento el código para que entiendas lo que hace y cómo lo hace:

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.28;

// Uncomment this line to use console.log
// import "hardhat/console.sol";

contract Lock {
    uint public unlockTime;
    address payable public owner;

    event Withdrawal(uint amount, uint when);

    constructor(uint _unlockTime) payable {
        require(
            block.timestamp < _unlockTime,
            "Unlock time should be in the future"
        );

        unlockTime = _unlockTime;
        owner = payable(msg.sender);
    }

    function withdraw() public {
        // Uncomment this line, and the import of "hardhat/console.sol", to print a log in your terminal
        // console.log("Unlock time is %o and block timestamp is %o", unlockTime, block.timestamp);

        require(block.timestamp >= unlockTime, "You can't withdraw yet");
        require(msg.sender == owner, "You aren't the owner");

        emit Withdrawal(address(this).balance, block.timestamp);

        owner.transfer(address(this).balance);
    }
}
```

El siguiente paso es compilar nuestro contrato, para esto corremos npx hardhat compile. Si todo salió bien veremos este output:

`Compiled 1 Solidity file successfully (evm target: paris).`

### Testeando nuestro contrato

Hardhat ya viene con Mocha, Chai y una versión especial de Ethers.js para probar todo lo que necesitamos. En otro artículo vamos a aprender más sobre crear pruebas para nuestros contratos pero por ahora, puedes ver que ya tenemos un archivo con varias pruebas en `test/Lock.js`. Te recomiendo que le eches un vistazo para que te familiarices con cómo se ve un archivo de pruebas de un smart contract en JavaScript.

A continuación, corre las pruebas: `npx hardhat test` y verás un mensaje de que todas las pruebas pasaron correctamente.

### Desplegando con Hardhat Ignition

¡Genial! Ya que escribimos y probamos a fondo nuestros contratos inteligentes, estamos listos para desplegarlos a una red. Por ahora vamos a usar Ignition y en otro artículo vamos a ver a fondo todas las opciones para customizar nuestros despliegues.

Si vas a la carpeta `ignition/modules/Lock.js` verás este código:

```javascript
// This setup uses Hardhat Ignition to manage smart contract deployments.
// Learn more about it at https://hardhat.org/ignition

const { buildModule } = require("@nomicfoundation/hardhat-ignition/modules");

const JAN_1ST_2030 = 1893456000;
const ONE_GWEI = 1_000_000_000n;

module.exports = buildModule("LockModule", (m) => {
  const unlockTime = m.getParameter("unlockTime", JAN_1ST_2030);
  const lockedAmount = m.getParameter("lockedAmount", ONE_GWEI);

  const lock = m.contract("Lock", [unlockTime], {
    value: lockedAmount,
  });

  return { lock };
});
```

Así que ahora corre el siguiente comando:

`npx hardhat ignition deploy ./ignition/modules/Lock.js`

y verás algo así:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1732931685874/a5ddc2e0-2ad7-483c-b9ad-155ee8aea87d.png align="center")

Como te diste cuenta, este despliegue se hizo a una red local simulada que Hardhat creó ‘*en el instante*’ para hacer el proceso de despliegue.

### Conclusión y próximos pasos

Así que ahora ya sabes cómo crear un proyecto de Hardhat, compilar contratos inteligentes, testearlos con JavaScript y desplegarlos a una red local, ¡gran trabajo!

En el siguiente artículo de esta serie te mostraré cómo desplegar a cualquier red de prueba (testnet) y mainnet de manera segura ¡vamos!
