---
title: "Variables de estado, visibilidad y mutabilidad"
datePublished: Wed Dec 11 2024 05:28:28 GMT+0000 (Coordinated Universal Time)
cuid: cm7sob1h5000109jpb9og0q8a
slug: variables-de-estado-visibilidad-y-mutabilidad
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733893188615/c0b710c5-f179-4982-912c-9cdab8fd5d17.png

---


Las **variables de estado** o state variables son una característica esencial de Solidity que te permite almacenar datos directamente en la blockchain. Hasta ahora, hemos trabajado principalmente con funciones puras que no interactúan con el estado de la blockchain. Sin embargo, si necesitas guardar información *on-chain* como puntajes en un juego o saldos financieros, tendrás que usar state variables. ¡Vamos a explorarlas!

---

## ¿Qué Son las Variables de Estado?

En Solidity, las variables de estado son aquellas que se declaran **fuera de las funciones** y quedan guardadas en la blockchain después de que una transacción finaliza. Ejemplo:

```solidity
contract StateVariables01 {
    uint256 internal x; // Variable de estado x

    function setX(uint256 newValue) public {
        x = newValue;
    }

    function getX() public view returns (uint256) {
        return x;
    }
}
```

En este ejemplo:

* `x` es una variable de estado que almacena un valor entero.
    
* `setX()` modifica el valor de `x`. Nota que como ésta función cambia el estado de la blockchain, no tiene el modificador `view` o `pure`.
    
* `getX()` lee el valor de `x`. Tiene el modificador `view` porque lee la blockchain pero no la modifica.
    

---

## Visibilidad: ¿Quién Puede Acceder a Estas Variables?

Cuando declaras una variable de estado, puedes definir su visibilidad con palabras clave como `public`, `internal` o `private`.

### Opciones de Visibilidad

* `public`:
    
    * Cualquier contrato o cuenta externa puede leer la variable.
        
    * El compilador genera automáticamente una función getter.
        
* `internal`:
    
    * Accesible solo dentro del contrato y en contratos que lo heredan.
        
* `private`:
    
    * Similar a `internal`, pero no accesible desde contratos derivados.
        

Por ejemplo, al cambiar la visibilidad de una variable a `internal` o `private`, notarás que los botones para interactuar con esa variable desaparecen en Remix.

```solidity
contract HelloWorld {
    string private text;

    constructor() {
        text = "Hello World";
    }

    function helloWorld() internal view returns (string memory) {
        return text;
    }
}
```

### Diferencia entre `internal` y `private`

La visibilidad `internal` permite que contratos heredados accedan a la variable o función, mientras que `private` restringe el acceso únicamente al contrato original.

---

## Modificadores de Mutabilidad: `pure`, `view`, y más

Los modificadores como `pure` y `view` definen si una función puede leer o modificar el estado de la blockchain.

### Tipos de Mutabilidad

* `pure`: No lee ni modifica el estado. Estas funciones son las más eficientes en términos de gas.
    
    ```solidity
    function addNumbers(uint256 a, uint256 b) public pure returns (uint256) {
        return a + b;
    }
    ```
    
* `view`: Puede leer el estado, pero no modificarlo. Llamar estas funciones directamente es gratuito.
    
    ```solidity
    function getX() public view returns (uint256) {
        return x;
    }
    ```
    
* `payable`: Permite que la función reciba Ether.
    
    ```solidity
    function deposit() public payable {
        // código para manejar depósitos
    }
    ```
    
* **Sin modificador o non-payable (default)**: Puede leer y modificar el estado de la blockchain.
    
    ```solidity
    function setX(uint256 newValue) public {
        x = newValue;
    }
    ```
    

---

## Ejemplo Práctico: Variables de Estado y Modificadores

Aquí tienes un contrato que combina variables de estado con diferentes visibilidades y modificadores de mutabilidad:

```solidity
contract ExampleContract {
    uint256 public balance; // Accesible externamente gracias a `public`

    function deposit(uint256 amount) public {
        balance += amount; // Modifica el estado
    }

    function getBalance() public view returns (uint256) {
        return balance; // Solo lee el estado
    }

    function calculateBonus(uint256 baseAmount) public pure returns (uint256) {
        return baseAmount * 10 / 100; // Operación pura
    }
}
```

---

## Buenas Prácticas y Consideraciones

1. **Sé explícito con la visibilidad**: Declara siempre la visibilidad de tus variables y funciones (`public`, `internal`, etc.) para evitar errores y mejorar la legibilidad.
    
2. **Recuerda que todo es público en la blockchain**: Aunque declares una variable como `private`, cualquier persona puede acceder a ella al analizar la blockchain.
    

---

## Conclusión

Las variables de estado son esenciales para almacenar datos en la blockchain. Junto con las opciones de visibilidad y los modificadores de mutabilidad, ofrecen una manera robusta y flexible de manejar el estado en tus contratos inteligentes.

¿List@ para experimentar con todo lo que hemos aprendido hasta ahora? ¡Prueba a implementar y desplegar algunos ejemplos en Remix! 🚀
