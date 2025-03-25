---
title: "Tipos de Datos en Solidity"
datePublished: Sat Dec 07 2024 03:42:06 GMT+0000 (Coordinated Universal Time)
cuid: cm7sob63m000409js86wx3atw
slug: tipos-de-datos-en-solidity
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733540988894/6ab76cd2-629b-45b1-8952-20bc95562bf1.png

---


¡Continuemos aprendiendo! En Solidity, cada variable y función tiene un tipo definido explícitamente. Si conoces lenguajes como Python o JavaScript sabrás que puedes declarar una variable y asignarle un string y después asignarle un número u otro valor. Si conoces Java o Typescript sabrás que acá tienes qué declarar si tu variable va a ser string, boolean u otra. Si no conoces ninguno de estos lenguajes no te preocupes, estamos aquí para aprender.

Por lo pronto, recuerda que en Solidity cada variables es de cierto *tipo*, vamos a ver los más usados.

## Tipos de Datos Más Usados

1. **Unsigned Integer (**`uint256`**):** Números enteros sin signo. Es decir solo podemos guardar el 0 y números positivos (`-300` sería un número negativo).
    
2. **Boolean (**`bool`**):** Variables que almacenan valores `true` o `false`.
    
3. **Address (**`address`**):** Tipo que almacena direcciones de wallets o contratos inteligentes en Ethereum.
    

Además de estos, Solidity incluye otros tipos como arrays, cadenas (strings) y estructuras (structs), que exploraremos más adelante.

### Ejemplo: Funciones con Diferentes Tipos de Retorno

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DataTypes01 {
    function getANumber() public pure returns (uint256) {
        uint256 x = 1;
        return x;
    }

    function getABoolean() public pure returns (bool) {
        bool y = true;
        return y;
    }

    function getAnAddress() public pure returns (address) {
        // La wallet de Vitalik Buterin
        address z = 0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045;
        return z;
    }

    function getAnotherAddress() public pure returns (address) {
        // Dirección del contrato de USDC
        address z2 = 0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48;
        return z2;
    }
}
```

Observa el código anterior (recuerda intentar escribir tú mism@ el código en Remix y probarlo). En este ejemplo, tenemos 4 funciones, cada una de ellas hace una cosa muy sencilla: guarda un valor hardcodeado en una variable y retorna esta variable.

Nota que siempre tienes qué poner en la firma de la función el tipo de dato que va a retornar tu función. Por ejemplo, intenta agregar esta función a tu código:

```solidity
    function getAddressFail() public pure returns (bool) {
        return 0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48;
    }
```

Verás que nos da un error porque la firma de tu función dice que va a regresar un `bool` y está regresando un `address`.

---

## Address (Dirección)

Recuerda que el tipo `address` representa una wallet o la dirección de un contrato. Siempre comienzan con `0x` más 40 caracteres entre `[0-9]` y `[a-f]` (hexadecimal).

**Checksum:** Las direcciones deben usar un checksum válido para evitar errores. Por ejemplo:

* Dirección sin checksum: `0xd8da6bf26964af9d7eed9e03e53415d37aa96045`
    
* Dirección con checksum: `0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045`
    

Si intentas usar una dirección sin checksum en Remix, podrías obtener un error como este:

```plaintext
SyntaxError: This looks like an address but has an invalid checksum.
```

Por ahora no te preocupes mucho por esto pero es bueno que aprendas a leer los errores. Si por alguna razón no puedes compilar tu código por este error, nota que el mismo Remix te da la versión correcta de la dirección que debes usar, solo lee el mensaje de error y ahí estará la respuesta:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733542323340/7acb8853-f0a3-408d-b15f-fd442e068eff.png align="center")

---

## uint256 (Entero sin Signo)

Un `uint256` es un entero sin signo que no puede almacenar números negativos. El número 256 indica que puede almacenar valores de hasta **256 bits**, es decir, entre `0` y `2^256 - 1`, es decir este numerotototote:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DataTypes02 {
    function getBiggestNumber() public pure returns (uint256) {
        return
            115792089237316195423570985008687907853269984665640564039457584007913129639935;
    }
}
```

Si intentas aumentar el último dígito a `6`, obtendrás un error porque excede el límite permitido.

Como principiantes, siempre que queramos declarar un número vamos a usar `uint256`, pero es bueno saber que hay `uint8`, `uint16`, `uint32`, etc.

---

## Boolean (bool)

Un `bool` almacena únicamente dos valores posibles: `true` o `false`. Es un tipo de dato básico y muy similar al de otros lenguajes de programación.

---

¡Ahora ya conoces los tipos de datos más comunes en Solidity! Recuerda practicar estos conceptos, probar el código en Remix y testear cualquier cosa que te dé curiosidad. Ahora sigamos explorando. 🚀
