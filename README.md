# Modelado_en_NetLogo
Este repositorio contiene una modificación del modelo original de NetLogo llamado "Moths" (Polillas). En este modelo, se simula el comportamiento de las polillas en respuesta a dos tipos de luces con diferentes longitudes de onda (luces rojas y azules). El objetivo de este modelo es explorar cómo las polillas reaccionan ante estos dos tipos de luces y analizar su comportamiento en diferentes condiciones de iluminación.

# Modelo de Polillas en NetLogo

## Integrantes
- Mariana Tellez Gutierrez
- Isabella Cardona Betancour
- Santiago Angel Franco

## Tipo: Comportamiento Biológico - Polillas (Moths)

## Modelo Base
Este modelo muestra polillas volando en círculos alrededor de una luz. Cada polilla sigue un conjunto de reglas simples. Ninguna de las reglas especifica que la polilla deba buscar y luego rodear una luz. Más bien, el patrón observado surge de la combinación del vuelo aleatorio de la polilla y las simples reglas de comportamiento.

Los científicos han propuesto varias explicaciones de por qué las polillas se sienten atraídas por las luces y luego las rodean. Por ejemplo, los científicos alguna vez creyeron que las polillas navegaban por el cielo orientándose hacia la luna, y que la atracción de las polillas hacia fuentes de luz terrestres cercanas (como una farola) surgía porque confunden las luces terrestres con la luna. Sin embargo, si bien esta explicación puede parecer razonable, no está respaldada por la evidencia científica disponible.

## Marco Teórico
En efecto, con los experimentos que realizó Sam Fabian, coautor del estudio e investigador de insectos del Imperial College de Londres (Reino Unido) se puede decir más bien que la luz artificial puede provocar un desajuste entre el sentido que tienen los insectos de la dirección de qué es arriba y la verdadera dirección de la gravedad.

Los científicos también realizaron varios de estos experimentos con luz en un laboratorio y obtuvieron resultados similares, aunque todavía no pueden descartar que otros factores también puedan estar contribuyendo a la tendencia de los insectos a enjambrar la luz.

Otras teorías han sugerido que la luz artificial ciega y desorienta a los insectos, que éstos se sienten atraídos por la radiación térmica de las luces o que piensan que la luz es una vía de escape, como un hueco en un arbusto.

Entonces después de ver algunas pruebas, artículos y un documental de Animal Planet tomamos que: las polillas tienden a ser atraídas más hacia la luz ultravioleta (UV) que a la luz visible normal. Este comportamiento se debe a que muchas especies de polillas tienen fotorreceptores en sus ojos que son particularmente sensibles a las longitudes de onda más cortas, como las del espectro ultravioleta. Además, en la naturaleza, algunas fuentes de luz ultravioleta, como la luna y las estrellas, pueden ser utilizadas por las polillas para la navegación nocturna. Por lo tanto, en ambientes controlados, se observa que las trampas de luz UV son más efectivas para atraer polillas en comparación con las trampas que utilizan luz visible de otras longitudes de onda.

## Explicación del Desarrollo

### Modelo Modificado
En nuestro modelo buscamos explicar este comportamiento biológico haciendo un enfoque a que las polillas vuelan en círculos y alrededor de los dos tipos de luz que incluimos: la luz violeta (representa la luz ultravioleta con menor longitud de onda), la luz roja (representa una onda con mayor longitud de onda), y de acuerdo con el tema de ondas electromagnéticas la luz violeta entonces será aquella que lleve mayor radiación térmica y atraerá mayormente a las polillas. Ninguna de las reglas especifica que la polilla deba buscar y luego rodear una luz. El patrón observado surge de la combinación del vuelo aleatorio de la polilla y las simples reglas de comportamiento, donde se trabaja una sensibilidad y luminancia para cada tipo de luz; dado que poseen un papel importante en el desarrollo del modelado y la modificación que se realizó.

### Descripción del Modelo
Esta es una modificación del modelo original de NetLogo llamado "Moths" (Polillas). En este modelo, se simula el comportamiento de las polillas en respuesta a dos tipos de luces con diferentes longitudes de onda:
- **Luces rojas**: Tienen mayor sensibilidad pero menor luminancia.
- **Luces moradas**: Tienen menor sensibilidad pero mayor luminancia.

El objetivo de este modelo es explorar cómo las polillas reaccionan ante estos dos tipos de luces y analizar su comportamiento en diferentes condiciones de iluminación.

Este modelo modificado nos permite:
- **Interactuar con diferentes longitudes de onda**: Las polillas muestran diferentes niveles de atracción hacia las luces rojas y moradas, proporcionando una visión más profunda de su comportamiento natural.
- **Observar resultados visuales**: Recorridos temporales visibles que ayudan a interpretar los patrones de movimiento y comportamiento de las polillas.

### Restricciones
Se quitó el deslizador de sensibilidad y el de luminancia, debido a que le asignamos unos valores fijos de las susodichas a las polillas y a las luces. 
Se sigue teniendo la posibilidad de escoger el número de luces (de 1 a 5); con la diferencia de que ahora se creará de forma aleatoria (el número de luces seleccionadas) de dos opciones; luces violetas y luces rojas. Que como explicamos con anterioridad, representarán luces con diferentes longitudes de onda (Las violetas con menor longitud de onda, y las rojas con mayor longitud de onda). 
Los factores de la sensibilidad y la luminosidad pasarán a ser valores intrínsecos fijos de las luces rojas y violetas; y naturalmente, cómo reaccionan las polillas hacía ellas.

## Bibliografía
Kiley Price. 31 ENE 2024. ¿Atrae la luz a las polillas? Un nuevo estudio refuta este conocimiento popular. Estudio de Sam Fabian et al, Imperial College de Londres (Reino Unido). Publicado y adaptado por National Geographic. Tomado de: [National Geographic](https://www.nationalgeographic.es/animales/2024/01/atrae-luz-polillas-insectos-nuevo-estudio-refuta-conocimiento-popular)

