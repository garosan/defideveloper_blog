---
title: "Cómo Instalar Foundry para Mac y Windows"
datePublished: Tue Oct 15 2024 23:57:33 GMT+0000 (Coordinated Universal Time)
cuid: cm7sfuns7000509l71j1mair7
slug: como-instalar-foundry-para-mac-y-windows
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729035607812/c8e73923-ab24-4c19-8ed0-a7251f215cf4.jpeg

---


---

# Cómo Instalar Foundry para Mac y Windows

Foundry es un conjunto de herramientas avanzadas para el desarrollo de contratos inteligentes y aplicaciones descentralizadas en Ethereum. En esta guía, te mostramos cómo instalar Foundry en Mac y en Windows. Para Windows, es necesario configurar el Subsistema de Windows para Linux (WSL) antes de la instalación. Este sistema nos permitirá tener un entorno de Linux de manera casi instantánea y la instalación de Foundry será mucho más sencilla.

## Instalación en Mac

### 1\. Instalar Homebrew (si no lo tienes instalado)

Homebrew es un gestor de paquetes para macOS que facilita la instalación de software. Para instalarlo, abre la terminal y ejecuta el siguiente comando:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2\. Instalar las dependencias de Foundry

Ejecuta el siguiente comando para instalar las herramientas necesarias, como `curl` y `git`:

```bash
brew install curl git
```

### 3\. Instalar Foundry

Para instalar Foundry, ejecuta el siguiente comando en la terminal:

```bash
curl -L https://foundry.paradigm.xyz | bash
```

Este comando descarga y ejecuta el script de instalación de Foundry. El script configurará la herramienta por ti.

### 4\. Configurar Foundry

Después de instalar Foundry, debes ejecutar el siguiente comando para inicializar las herramientas de Foundry:

```bash
foundryup
```

Este comando descargará e instalará las últimas versiones de Foundry, Forge y Cast.

### 5\. Verificar la instalación

Para asegurarte de que Foundry esté instalado correctamente, ejecuta el siguiente comando:

```bash
forge --version
```

Si ves la versión de Foundry en la terminal, la instalación fue exitosa.

---

## Instalación en Windows

### 1\. Instalar el Subsistema de Windows para Linux (WSL)

Para usar Foundry en Windows, primero debes instalar WSL, lo que te permitirá usar un entorno de Linux dentro de Windows.

#### 1.1 Habilitar WSL

Abre una terminal de PowerShell como administrador y ejecuta el siguiente comando:

```bash
wsl --install
```

Este comando instalará WSL 2 junto con Ubuntu como la distribución predeterminada. Si ya tienes WSL instalado, puedes actualizar a WSL 2 con el siguiente comando:

```bash
wsl --set-default-version 2
```

#### 1.2 Reiniciar el sistema

Una vez que WSL esté instalado, se te pedirá que reinicies tu computadora.

#### 1.3 Configurar WSL

Después de reiniciar, abre PowerShell nuevamente y ejecuta el siguiente comando para asegurarte de que Ubuntu sea tu distribución predeterminada:

```bash
wsl --set-default ubuntu
```

### 2\. Instalar las dependencias en WSL

Abre la terminal de Ubuntu dentro de WSL e instala las dependencias necesarias para Foundry, como `curl` y `git`:

```bash
sudo apt update
sudo apt install curl git build-essential
```

### 3\. Instalar Foundry

Dentro de la terminal de Ubuntu, ejecuta el siguiente comando para instalar Foundry:

```bash
curl -L https://foundry.paradigm.xyz | bash
```

### 4\. Configurar Foundry

Después de la instalación, ejecuta el siguiente comando para configurar Foundry y sus herramientas:

```bash
foundryup
```

### 5\. Verificar la instalación

Por último, verifica que Foundry esté instalado correctamente con el siguiente comando:

```bash
forge --version
```

Si todo salió bien, verás la versión de Forge en la terminal.

---

## Conclusión

Ya sea en macOS o Windows, con estos pasos podrás tener Foundry instalado y listo para usar. Esto nos permitirá usar las mismas librerías y software que utilizan los profesionales para desarrollar dapps a la vez que podremos trabajar en los ejercicios de [la guía que estaremos siguiendo](https://www.rareskills.io/learn-solidity) y podremos verificar si los ejercicios están bien hechos. Para Windows, recuerda que primero debes configurar WSL para trabajar en un entorno Linux. Ahora puedes comenzar a desarrollar tus proyectos de contratos inteligentes con Foundry.
