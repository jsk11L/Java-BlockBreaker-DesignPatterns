# BlockBreaker con Patrones de Diseño (Java & LibGDX)

![Java](https://img.shields.io/badge/Java-8%2B-007396?style=for-the-badge&logo=java)
![LibGDX](https://img.shields.io/badge/LibGDX-1.11.0-bA2727?style=for-the-badge&logo=libgdx)

Un clon del clásico juego "Breakout" (Arkanoid) desarrollado en Java con el framework LibGDX.

El objetivo principal de este proyecto no fue solo crear un juego, sino **demostrar la aplicación práctica de patrones de diseño de software (GoF)** para crear una base de código mantenible, escalable y robusta.

---

## 🎮 Demo
*(¡Te recomiendo grabar un GIF corto de tu juego y ponerlo aquí! Sube el GIF al repositorio y reemplaza esta línea con `![Demo del Juego](nombre-de-tu-gif.gif)`)*

---

## 🚀 Características

* Juego clásico de romper ladrillos con paleta y pelota.
* Múltiples niveles de dificultad (Fácil, Medio, Difícil).
* Diferentes tipos de bloques (normales y bloques duros que requieren 2 golpes).
* Power-ups que caen al romper bloques (velocidad rápida y lenta).
* Gestión de puntuación, vidas y sistema de Pausa/Reanudar.
* Gestión centralizada de sonidos y música.

---

## 🏛️ Arquitectura y Patrones de Diseño

El núcleo del proyecto es la implementación de los siguientes patrones:

### 1. Patrón Singleton
Utilizado para garantizar una única instancia global de los gestores de recursos.
* `ResourceManager`: Carga y provee todas las texturas, música y sonidos, evitando cargarlos múltiples veces en memoria.
* `SoundManager`: Controla la reproducción de música y sonidos, permitiendo silenciarlos globalmente.

### 2. Patrón Strategy
Usado para definir una familia de algoritmos (comportamientos de la pelota) y hacerlos intercambiables.
* `BallBehavior` (Interfaz): Define el método `apply()`.
* `NormalBehavior`, `FastBehavior`, `SlowBehavior` (Clases Concretas): Implementan la interfaz para modificar la velocidad y color de la pelota.

### 3. Patrón Template Method
Define el esqueleto de un algoritmo (creación de nivel) en una superclase, permitiendo a las subclases redefinir ciertos pasos.
* `LevelTemplate` (Clase Abstracta): Contiene el método `playLevel()` que llama a `initializeLevel()` y `setupBlocks()`.
* `EasyLevel`, `MediumLevel`, `HardLevel` (Clases Concretas): Implementan los métodos abstractos para definir la velocidad de la pelota y la configuración de bloques específica de cada nivel.

### 4. Patrón Builder
Usado para construir objetos complejos (niveles) paso a paso.
* `LevelBuilder` (Interfaz): Define los pasos para construir un nivel (dificultad, tipo de bloques, etc.).
* `ConcreteLevelBuilder`: Implementa la interfaz y es utilizado por el `GameManager` para ensamblar niveles dinámicamente.

---

## 🛠️ Tecnologías Utilizadas

* **Java (JDK 8)**
* **LibGDX** (Framework de desarrollo de juegos)
* **Gradle** (Gestor de dependencias y build)

---

## 🔧 Cómo Ejecutar el Proyecto

Este proyecto usa Gradle. Puedes ejecutarlo fácilmente desde la línea de comandos en la raíz del proyecto.

```bash
# Clonar el repositorio
git clone [https://github.com/tu-usuario/Java-BlockBreaker-DesignPatterns.git](https://github.com/tu-usuario/Java-BlockBreaker-DesignPatterns.git)
cd Java-BlockBreaker-DesignPatterns

# Ejecutar la versión de escritorio
./gradlew desktop:run
