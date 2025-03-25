---
title: "Strings (cadenas) en Solidity"
datePublished: Wed Dec 11 2024 04:53:59 GMT+0000 (Coordinated Universal Time)
cuid: cm7sob2ge000108l17ozq8xbs
slug: strings-cadenas-en-solidity
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733892123631/0440906b-34b5-463b-81d8-4537c4c2fbb9.png

---


Los **strings** en Solidity comparten muchas características con los arrays, ya que bajo el capó son arrays de bytes. Sin embargo, trabajar con strings tiene sus propias particularidades en Solidity. ¡Vamos a explorarlas!

---

## Uso Básico de Strings

En Solidity, puedes definir una función que reciba un string como entrada y lo retorne como salida:

```solidity
contract ExampleContract {
    function echo(string calldata input) public pure returns (string memory) {
        return input;
    }
}
```

Este tipo de funciones es útil cuando necesitas procesar o retornar información textual.

---

## Concatenación de Strings

Una curiosidad de Solidity, es que no soportaba concatenación de strings hasta febrero de 2022, cuando salió la versión 0.8.12. A partir de esta versión, puedes usar `string.concat`:

```solidity
pragma solidity ^0.8.12;

contract ExampleContract {
    function greetUser(string calldata user) public pure returns (string memory) {
        return string.concat("Hello, ", user);
    }
}
```

Esta es una pequeña muestra de que Solidity está optimizado para manejar números más que texto.

---

## Limitaciones de los Strings

### No se pueden indexar

A diferencia de lenguajes como JavaScript o Python, no puedes acceder a un carácter específico en un string mediante indexación:

```solidity
pragma solidity ^0.8.12;

contract BadContract {
    function getFirstCharacter(string calldata input) public pure returns (string memory) {
        return input[0]; // Esto producirá un error
    }
}
```

### Sin `.length`

Solidity no permite obtener la longitud de un string directamente con `.length`. Esto se debe a que los strings son representados como bytes y pueden incluir caracteres Unicode, lo que complica la medición.

---

Los strings en Solidity tienen algunas limitaciones que dan cuenta de que los smart contracts fueron concebidos en primera instancia para trabajar principalmente con números, no texto. Sin embargo, entender cómo manejarlos te será útil para casos específicos, como mensajes descriptivos o identificadores únicos. 🚀

Ahora ya dominamos los arrays y los strings, y estamos listos para aplicar estas estructuras de datos y aprender más en nuestro camino como blockchain devs, ¡sigamos explorando!
