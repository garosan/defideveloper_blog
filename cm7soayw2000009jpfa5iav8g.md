---
title: "Mappings anidados en Solidity"
datePublished: Wed Dec 11 2024 16:01:52 GMT+0000 (Coordinated Universal Time)
cuid: cm7soayw2000009jpfa5iav8g
slug: mappings-anidados-en-solidity
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733932554414/8ec490b8-46b4-4b79-8da2-d4f72821785c.png

---


Los **nested mappings** (mapeos anidados) son una poderosa herramienta en Solidity para trabajar con estructuras de datos más complejas de claves y valores. En este artículo, exploraremos cómo usarlos de manera efectiva y algunas de sus peculiaridades.

---

## ¿Qué Son los Nested Mappings?

Un nested mapping es simplemente un mapping cuyo valor es otro mapping. Esto te permite almacenar datos en estructuras jerárquicas, como una matriz de datos indexados por múltiples claves.

### Ejemplo Básico

Aquí un ejemplo de cómo declarar y usar un nested mapping en Solidity:

```solidity
contract NestedMappings01 {

    mapping(uint256 => mapping(uint256 => uint256)) public nestedMap;

    function setNestedMap(
        uint256 key1,
        uint256 key2,
        uint256 finalValue
    ) public {
        nestedMap[key1][key2] = finalValue;
    }

    function getNestedMap(
        uint256 key1,
        uint256 key2
    ) public view returns (uint256) {
        return nestedMap[key1][key2];
    }
}
```

En este ejemplo:

* `nestedMap` asocia una clave `key1` a otro mapping, que a su vez asocia `key2` con un valor final.
    
* `setNestedMap` permite establecer un valor en el mapping anidado.
    
* `getNestedMap` recupera el valor almacenado en las claves `key1` y `key2`.
    

---

## Visualización de Nested Mappings

Supongamos que llamamos a `setNestedMap(1, 2, 100)`. El resultado se vería así en pseudocódigo:

```javascript
{
  1: {
    2: 100
  }
}
```

Aquí, `1` es la clave del primer mapping, que apunta a un segundo mapping. En ese segundo mapping, `2` es la clave que apunta al valor `100`.

---

## Restricciones y Peculiaridades de los Nested Mappings

### 1\. **Los Nested Mappings Públicos No Funcionan Como Esperas**

Si declaras un mapping como `public`, Solidity genera automáticamente una función getter para acceder a sus valores. Sin embargo, en el caso de nested mappings, el getter requiere que proporciones **todas las claves necesarias** para recuperar un valor.

Por ejemplo, con el nested mapping `nestedMap`, el getter generado automáticamente permite llamar a `nestedMap(1, 2)` para obtener el valor asociado. No puedes acceder al mapping interno completo.

#### Solución: Usa Funciones Envolventes

Para mayor control, puedes declarar el mapping como `private` y crear funciones públicas que manejen el acceso:

```solidity
contract NestedMappings02 {
    mapping(uint256 => mapping(uint256 => uint256)) private nestedMap;

    function setNestedMap(uint256 key1, uint256 key2, uint256 finalValue) public {
        nestedMap[key1][key2] = finalValue;
    }

    function getNestedMap(uint256 key1, uint256 key2) public view returns (uint256) {
        return nestedMap[key1][key2];
    }
}
```

---

### 2\. **No Puedes Iterar Sobre Nested Mappings**

Al igual que con los mappings simples, Solidity no permite iterar sobre los keys de un nested mapping. Esto se debe a que todas las claves posibles son válidas y retornan su valor predeterminado si no han sido definidas.

---

## Casos de Uso de Nested Mappings

Los nested mappings son muy útiles para modelar relaciones complejas. Algunos ejemplos comunes incluyen:

1. **Sistemas de Permisos**: Un mapping puede asociar direcciones de usuarios con permisos específicos.
    
    ```solidity
    mapping(address => mapping(string => bool)) private permissions;
    ```
    
2. **Balances Detallados**: Puedes almacenar balances separados por categorías para cada usuario.
    
    ```solidity
    mapping(address => mapping(string => uint256)) private balances;
    ```
    
3. **Datos Jerárquicos**: Estructuras como tablas relacionales se pueden modelar fácilmente con nested mappings.
    

---

## Conclusión

Los nested mappings son una herramienta versátil en Solidity para manejar datos complejos. Aunque tienen limitaciones, como la imposibilidad de iterar sobre las claves o acceder a mappings internos completos a través de getters automáticos, estas restricciones se pueden manejar con buenas prácticas de diseño.

Si estás modelando relaciones jerárquicas o estructuras multi-clave, los nested mappings pueden ser tu mejor aliado. ¡Prueba los ejemplos en Remix para experimentar con estas ideas! 🚀
