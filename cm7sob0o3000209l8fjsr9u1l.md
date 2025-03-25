---
title: "Manipulación avanzada de arrays"
datePublished: Wed Dec 11 2024 15:00:36 GMT+0000 (Coordinated Universal Time)
cuid: cm7sob0o3000209l8fjsr9u1l
slug: manipulacion-avanzada-de-arrays
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733928809035/ee4653a4-cf61-4c97-a8fa-739766f60665.png

---


En Solidity, los arrays almacenados en **storage** tienen un comportamiento especial que permite manipularlos directamente en la blockchain. Esto incluye agregar, eliminar, y modificar elementos. Estas operaciones se vuelven cruciales cuando los arrays son persistidos en el estado de nuestro smart contract.

¡Vamos a explorar cómo funciona todo esto! 🚀

---

## Operaciones Básicas en Arrays de Storage

Aquí tienes un ejemplo básico de cómo trabajar con arrays almacenados en **storage**:

```solidity
contract ArraysInStorage01 {
    uint256[] public myArray;

    function setMyArray(uint256[] calldata newArray) public {
        myArray = newArray; // Asigna el contenido de newArray a myArray
    }

    function addToArray(uint256 newItem) public {
        myArray.push(newItem); // Agrega un elemento al final
    }

    function removeFromArray() public {
        myArray.pop(); // Elimina el último elemento
    }

    function getLength() public view returns (uint256) {
        return myArray.length; // Devuelve la longitud del array
    }

    function getEntireArray() public view returns (uint256[] memory) {
        return myArray; // Devuelve el array completo
    }
}
```

### Interacción en Remix

1. `setMyArray`: Establece un nuevo array, por ejemplo, `[1, 2, 3]`.
    
2. `addToArray`: Agrega un nuevo número al final, como `4`. El array se convierte en `[1, 2, 3, 4]`.
    
3. `removeFromArray`: Elimina el último elemento. El array ahora es `[1, 2, 3]`.
    
4. `getLength`: Devuelve `3`, la longitud del array.
    
5. `getEntireArray`: Retorna `[1, 2, 3]`.
    

---

## Acceso Público a Arrays

Cuando un array es declarado como `public`, Solidity genera automáticamente una función getter que permite acceder a sus valores. Sin embargo, este getter solo devuelve elementos individuales, no el array completo.

Por ejemplo, al llamar `myArray(0)` obtendrás el primer elemento, pero si necesitas todo el array, debes usar una función como `getEntireArray`.

### ¿Qué pasa con `pop()`?

La función `pop()` elimina el último elemento del array y reduce su longitud, pero **no retorna el valor eliminado** como es común en otros lenguajes de programación.

---

## Eliminando Elementos del Array

Solidity no permite eliminar un elemento en el medio de un array y ajustar automáticamente su longitud. Si intentas hacerlo, el valor será **reemplazado por cero**, pero la longitud del array no cambiará.

```solidity
contract ExampleContract {
    uint256[] public myArray;

    function removeAt(uint256 index) public {
        delete myArray[index]; // El elemento se convierte en 0
    }
}
```

### Pop and Swap: Una Solución Común

Si necesitas eliminar un elemento y reducir la longitud del array, puedes usar el patrón **pop and swap**. Este método reemplaza el elemento a eliminar con el último elemento y luego utiliza `pop()` para reducir la longitud:

```solidity
contract ExampleContract {
    uint256[] public myArray;

    function popAndSwap(uint256 index) public {
        uint256 valueAtTheEnd = myArray[myArray.length - 1];
        myArray[index] = valueAtTheEnd; // Reemplaza con el último elemento
        myArray.pop(); // Reduce la longitud
    }
}
```

Este enfoque no preserva el orden original del array, pero es eficiente en términos de gas.

---

## Conclusión

Trabajar con arrays en **storage** te brinda una gran flexibilidad para manejar datos en la blockchain. Desde agregar y eliminar elementos hasta manipular arrays completos, estas herramientas son esenciales para desarrollar smart contracts robustos.

Sin embargo, es importante tener en cuenta las limitaciones, como la falta de soporte para eliminar elementos en medio del array mientras se preserva su orden.

¡Experimenta con estos conceptos en Remix y observa cómo puedes usarlos en tus próximos proyectos de Solidity! 🚀
