---
title: "Hello Solidity!"
datePublished: Wed Oct 09 2024 05:46:37 GMT+0000 (Coordinated Universal Time)
cuid: cm7sfup0r000409l84jsdftzc
slug: hello-solidity
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1728452878110/c0ba04c6-c583-4cc2-848f-a0672e48a4b5.webp

---


No se puede empezar a aprender algo en programación sin hacer un Hello, world!  
  
Para aprender lo básico de Solidity hay una sola herramienta que nos permitirá hacer todo en línea sin preocuparnos de nada más. Esta herramienta se llama Remix:

[**remix.ethereum.org**](http://remix.ethereum.org)  
  
Asegúrate siempre de estar en esa URL y no en otra que esté tratando de hacerse pasar por Remix.  
  
Este será nuestro primer contrato inteligente:

```solidity
contract HelloWorldContract {

    function helloWorld() public pure returns (uint256) {
            return 100;
    }

    function returnBool() public pure returns (bool) {
            return true;
    }
}
```

Adentro de Remix, haz click derecho en `contracts` y luego en *New File.* Todos los archivos de Solidity deben tener la extensión `.sol`, así que llamemos este archivo `HelloWorld.sol`. Ahora copia y pega el código de arriba, o trata de escribirlo tú mismo.  
  
El siguiente paso es compilar el código para lo cual solo tenemos qué hacer `CTRL + S`.

Ahora, hay qué dar click en el símbolo de Ethereum en el menú de la izquierda, y click en el botón naranja que dice *Deploy*.

Si hiciste todo bien, en la parte de abajo, justo debajo de donde dice *Deployed/Unpinned Contracts* encontrarás tu contrato desplegado en una blockchain virtual, y podrás interactuar con él.  
  
Verás un botón azul que dice *helloWorld* y otro que dice *returnBool*. Haz click en ellos y ve lo que resulta de darles click. Ahora haz hecho tu primer smart contract en Remix!

![Foto tomada de artículo de RareSkills](https://www.rareskills.io/wp-content/uploads/2024/09/c0c19a_4776ae8f1f634e8ebb309e62ef0d8ebb~mv2.png align="left")

[Fuente: Artículo](https://remix.ethereum.org/) [de Rare Skills](https://www.rareskills.io/learn-solidity/remix-solidity)
