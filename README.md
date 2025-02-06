# Optimización de Campaña de Marketing Online con el Bandido Multi-Brazo (Multi-Armed Bandit)

[![GitHub](https://img.shields.io/badge/GitHub-View%20on%20GitHub-blue?logo=github)](https://github.com/DiegoLerma/multi-armed-bandit.git)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

<img src="https://static.vecteezy.com/system/resources/thumbnails/027/303/356/small_2x/digital-marketing-commerce-online-sale-concept-promotion-of-products-or-services-through-digital-channels-search-engine-social-media-email-website-digital-marketing-strategies-and-goals-seo-ppc-photo.jpg" alt="Marketing Online" width="600"/>

## Introducción

Este proyecto aborda un problema clásico en la optimización de campañas de marketing online: **¿cómo identificar la mejor imagen para un anuncio, maximizando el número de clics?**  Para resolverlo, empleamos el algoritmo del **Bandido Multi-Brazo (Multi-Armed Bandit, MAB)**, una técnica de aprendizaje por refuerzo que equilibra la *exploración* de nuevas opciones y la *explotación* de las que ya han demostrado ser efectivas.

Este enfoque es particularmente útil en entornos dinámicos, como la publicidad online, donde las preferencias de los usuarios pueden cambiar rápidamente.

## ¿Qué es el Bandido Multi-Brazo (MAB)?

Imagina que estás frente a una fila de máquinas tragamonedas (o "bandidos" de un solo brazo). Cada máquina tiene una probabilidad desconocida de dar una recompensa. Tu objetivo es maximizar tus ganancias a largo plazo.  ¿Cómo decides a qué máquina jugar?

<img src="https://media.licdn.com/dms/image/v2/C4D12AQEGFgjM7YZpYg/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1618176729724?e=2147483647&v=beta&t=tJaR7QLD9jbkYAdep9zrwFFzl3RAJyKnr6MtDqARkoc" alt="Bandido Multi-Brazo" width="400"/>

El problema del Bandido Multi-Brazo se basa en esta analogía.  Cada "brazo" representa una acción posible (en nuestro caso, mostrar una imagen de anuncio diferente).  El algoritmo MAB aprende iterativamente cuál es el mejor brazo (la mejor imagen) a medida que interactúa con el entorno (los usuarios que hacen clic o no en el anuncio).

### Estrategias MAB Comunes

Existen varias estrategias para resolver el problema del MAB, cada una con su propia forma de equilibrar exploración y explotación:

*   **Epsilon-Greedy:**  Con una probabilidad *ε* (épsilon), se elige una acción aleatoria (exploración).  Con una probabilidad *1 - ε*, se elige la acción que, hasta ahora, ha tenido la mayor recompensa promedio (explotación).
*   **Upper Confidence Bound (UCB):**  Se elige la acción que maximiza una combinación de la recompensa promedio observada y una medida de incertidumbre.  Esto favorece la exploración de acciones con menos datos.
*   **Thompson Sampling:**  Se utiliza un enfoque bayesiano para asignar una probabilidad a cada acción de ser la óptima.  Se muestrea una acción de acuerdo con estas probabilidades.

## Propósito del Notebook

Este notebook de Jupyter tiene como objetivo:

1.  **Demostrar la aplicación práctica del algoritmo Epsilon-Greedy del Bandido Multi-Brazo** para optimizar una campaña de marketing online.
2.  **Experimentar con diferentes valores de *ε*** para entender su impacto en el equilibrio exploración-explotación.
3.  **Identificar la imagen del anuncio** que genera el mayor número de clics.
4.  **Comparar el rendimiento** de una estrategia puramente de explotación (sin exploración) con estrategias que sí exploran.

## Cómo Inicializar el Proyecto

1.  **Clonar el Repositorio:**
    ```bash
    git clone https://github.com/DiegoLerma/multi-armed-bandit.git
    cd multi-armed-bandit
    ```

2.  **Crear un Entorno Virtual (Recomendado):**
    ```bash
    python3 -m venv .venv
    source .venv/bin/activate  # En Linux/macOS
    .venv\\Scripts\\activate  # En Windows
    ```

3.  **Instalar las Dependencias:**
    ```bash
    pip install -r requirements.txt
    ```
    (El archivo `requirements.txt` debería contener: `numpy`, `pandas`, `matplotlib`, `jupyter`)

4.  **Ejecutar el Notebook:**
    ```bash
    jupyter notebook multi-armed-bandit.ipynb
    ```
     o
    ```bash
     jupyter lab
    ```

    Esto abrirá el notebook en tu navegador web.  Puedes ejecutar las celdas de código de forma interactiva y observar los resultados.

## Resumen de las Respuestas

El notebook explora las siguientes preguntas clave:

1.  **¿Cuál es el valor de *ε* que maximiza el número de clics de la imagen ganadora?**

    *   **Respuesta:**  Los mejores valores de *ε* suelen estar entre 0.01 y 0.1.  Un valor demasiado alto lleva a una explotación prematura, mientras que un valor demasiado bajo resulta en una exploración insuficiente.

2.  **¿Cuál es la imagen que, tras la optimización, obtiene el mayor número de clics y cuántos clics son?**

    *   **Respuesta:** La imagen ganadora y el número de clics varían en cada ejecución debido a la naturaleza aleatoria del experimento. El notebook proporciona el código para identificar la imagen ganadora y sus clics en cada caso.

3.  **¿Qué resultado se obtiene al aplicar una ratio de explotación del 100% (es decir, sin exploración)?**

    *   **Respuesta:** Una estrategia puramente de explotación (ε = 1) generalmente conduce a un rendimiento subóptimo.  El algoritmo se "atasca" en la primera opción que parece buena, sin explorar otras que podrían ser mejores a largo plazo.  Esto se traduce en una pérdida significativa de clics en comparación con estrategias que incluyen exploración.

## Contribuciones

¡Las contribuciones son bienvenidas! Si encuentras errores, tienes ideas para mejorar el código o quieres agregar nuevas estrategias MAB, no dudes en abrir un *issue* o enviar un *pull request*.