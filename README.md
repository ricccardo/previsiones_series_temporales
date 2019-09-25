# previsiones_series_temporales

## INTRODUCCIÓN

En este trabajo se analizan distintos métodos para realizar previsiones con series temporales. Cuando se realiza una previsión se analizan los datos históricos y se estima una demanda futura para un producto o servicio. Es una actividad esencial para la toma  de decisiones en las distintas áreas funcionales de la empresa.
Los datos de entrada contienen el número de pasajeros diarios de una compañía de trenes en un período de dos años. El objetivo es realizar una predicción para los siguientes siete meses.

## SERIE TEMPORAL

Una serie temporal es una colección de observaciones de una variable realizadas de forma secuencial en el tiempo en las que el orden de observación es importante. 
Podría pensarse que, como la variable dependiente es numérica, puede emplearse la técnica de regresión lineal para realizar la predicción. Pero la serie temporal tiene unas características propias que requieren un modelo específico.
Se ha de tener en cuenta el orden temporal de las observaciones. Los métodos estadísticos basados en la independencia de las observaciones no son válidos para el análisis de series temporales porque las observaciones en un instante de tiempo dependen de los valores de la serie en el pasado.
     
Los objetivos que se pueden plantear al analizar una serie temporal pueden ser:
    a) Descripción de las caracterı́sticas de la serie en términos de sus componentes.
       Se basa en la idea de que el comportamiento de una variable en el tiempo es el resultado de la integración de
       tres componentes (aunque no siempre aparecen todos):
            1. Tendencia: Se puede definir como un cambio a largo plazo que se produce en relación al nivel medio, o el
               cambio a largo plazo de la media. La tendencia se identifica con un movimiento suave de la serie a largo 
               plazo.
            2. Efecto Estacional: Muchas series temporales presentan cierta periodicidad o dicho de otro modo, variación
               de cierto periodo (anual, mensual ...). 
            3. Componente Aleatoria: Una vez identificados los componentes anteriores y después de haberlos eliminado, 
               persisten unos valores que son aleatorios. 
       La tendencia  y la componente estacional constituyen la señal o parte determinística, la parte aleatoria es el 
       ruido.
    b) Predicción de futuros valores de las variables.
       Se pretende identificar un patrón en el comportamiento pasado de la variable, es decir, obtener el mecanismo que 
       la genera para tener un mejor conocimiento de la misma en el tiempo. Si las condiciones estructurales que 
       conforman la serie permanecen constantes, se podrá predecir el comportamiento futuro.
       
El estudio de series temporales puede tener dos enfoques:
    a) Modelos clásicos o deterministas,
    b) Modelos ARIMA.

## MODELOS LINEALES CLÁSICOS

Explican el comportamiento de una variable temporal usando para ello sólo su propia historia pasada y reciente.
Son sólo adecuados para realizar previsiones a corto plazo, pero son métodos sencillos y ofrecen resultados satisfactorios aunque no se disponga de un gran número de datos históricos.

Según las características de la serie encontraremos diferentes modelos:
    a) Modelos aplicables a series sin tendencia ni estacionalidad:
        1. Modelo ‘naive’ o ingenuo.
           Se da importancia únicamente al último de los datos de que disponemos, ignorando el resto.
        2. Modelo de medias móviles.
           Se basa en considerar únicamente las últimas observaciones. De esta manera se da el mismo peso a los últimos
           datos y cero al resto, mediante un procedimiento de medias móviles. Este procedimiento no es tan extremo
           como los anteriores y, al sustituir cada dato por una media de los últimos, la serie se suaviza y se elimina 
           ruido, obteniendo el patrón subyacente de la misma. Cuantas más observaciones relevantes tomemos al aplicar 
           este tipo de ajuste más se suavizará la serie.    
        3. Modelo de suavizado exponencial simple.
           Consiste en dar importancia a todos los datos anteriores, pero concediendoles diferentes pesos. Los datos más
           relevantes a la hora de efectuar una previsión son los últimos de los que se dispone, de forma que este 
           método considera que la importancia disminuye conforme nos alejamos de ellos.
    b) Modelo aplicable a series no estacionales con tendencia: Modelo de suavizado exponencial doble o de Holt.
    c) Modelo aplicable a series con tendencia y estacionalidad: Modelo de suavizado exponencial triple o de Holt-
       Winters.


## MODELOS ARIMA

Box y Jenkins han desarrollado modelos estadísticos para series temporales que tienen en cuenta la dependencia existente entre los datos, de modo que cada observación en un momento dado es modelada en función de los valores anteriores. Los modelos se conocen con el nombre genérico de ARIMA (AutoRegresive Integrated Moving Average), que deriva de sus tres componentes AR (Autoregresivo), I (Integrado) y MA (Medias Móviles).
Los modelos ARIMA permiten describir un valor como una función lineal de datos anteriores y errores debidos al azar, y pueden incluir un componente estacional. El número de observaciones analizadas ha de ser mayor que en los modelos clásicos, se recomiendan como mínimo 50.

La base teórica de estos modelos se fundamenta en el concepto de proceso estocástico. 
Un proceso estocástico es un conjunto de variables aleatorias relacionadas entre sı́  que siguen una ley de distribución conjunta. Una serie temporal se puede interpretar como una realización muestral de un proceso estocástico, que se observa únicamente para un número finito de periodos, formada por una muestra de tamaño 1 de cada una de las variables aleatorias que forman el proceso.
El objetivo es determinar qué proceso estocástico ha sido capaz de generar la serie temporal con el fin de modelizar el comportamiento de la serie y predecir en el futuro. Si se quieren conseguir métodos de predicción consistentes, no se puede utilizar cualquier tipo de proceso estocástico, sino que es necesario que la estructura probabilı́stica del mismo sea estable en el tiempo. Esto es, el proceso ha ser estacionario. 

El concepto de estacionariedad se puede caracterizar bien en términos de la función de distribución o de los momentos del proceso. En el primer caso, se hablará de estacionariedad en sentido estricto y, en el segundo, de estacionariedad en sentido amplio.
Un proceso estocástico es estacionario en sentido amplio si:
    a) Es estacionario en media, es decir, todas las variables aleatorias del proceso tienen la misma media.
    b) Es estacionario en varianza, esto es, todas las variables aleatorias tienen la misma varianza.
    c) Las autocovarianzas solo dependen del número de periodos de separación entre las variables y no del tiempo.
Si un proceso estocástico es estacionario en sentido amplio y su distribución es normal, es estacionario en sentido estricto.
Dada la complejidad de cálculo de la estacionariedad estricta, suele emplearse la estacionariedad en sentido amplio.

La estacionariedad se puede evaluar de dos maneras:
    a) Mediante una gráfica. Al trazar la desviación estándar y la media junto con los puntos de datos originales, la
       serie será estacionaria si ambos son algo constantes en el tiempo.
    b) Realizando un test estadístico, en este caso la prueba de Dickey-Fuller.
    
Test de Dickey-Fuller:
Anteriormente se han definido los modelos ARIMA como los que permiten describir un valor como una función lineal de datos anteriores y errores debidos al azar. La ecuación que describe ese comportamiento sería
      Xt = coef * Xt-1 + Et,
donde la variable Xt dependería del valor de la misma variable en un momento anterior (Xt-1) multiplicado por un coeficiente constante (coef) más el ruido o componente aleatoria (Et).
Si el coeficiente es igual a 1 (esto es, hay raíz unitaria) la variación de la variable sólo dependerá de la componente aleatoria y la serie no es estacionaria. 
En la práctica, de trata de una prueba de contraste. La hipótesis nula es que la serie tiene raíz unitaria y, por lo tanto, no es estacionaria; la hipótesis alternativa consiste en rechazar la hipótesis nula , así que  la serie es estacionaria.
El resultado de la prueba arroja un estadístico y unos valores críticos para distintos niveles de confianza. Si el estadístico es menor que el valor crítico deseado, se rechaza la hipótesis nula y la serie es estacionaria. En caso contrario se mantiene la hipótesis nula y la serie no es estacionaria.

Si la serie no es estacionaria se le pueden aplicar transformaciones:
    a) Transformación logarítmica para estabilizar la varianza,
    b) Diferenciación simple para eliminar la tendencia. Se calculan las diferencias existentes entre cada valor y el 
       anterior de la serie, a excepción del valor más antiguo de la serie. Por tanto, la serie diferenciada tendrá un
       valor menos que la serie original.
    c) Diferenciación estacional para eliminar la estacionalidad. Es idéntica a la diferenciación simple, excepto en que
       se calculan las diferencias existentes entre cada valor y el valor estacional anterior.
Si se usa la diferenciación simple o estacional de forma simultánea con la transformación logarítmica o de raíz cuadrada, siempre se aplicará primero la transformación de estabilización de la varianza. Si se usan la diferenciación simple y estacional, los valores de la serie resultante son iguales independientemente de si se aplica primero una diferenciación u otra.

El proceso también ha de ser ergódico. Para explicar este concepto es necesario definir antes la función de autocorrelación.
Se denomina autocorrelación de orden k, ρk, a la correlación de cualesquiera dos variables aleatorias del proceso estocástico, distanciadas k instantes de tiempo. No tiene unidades por definición y toma valores entre -1 y 1. Si es 0 no existe relación lineal entre las observaciones. Si es 1 existe relación lineal perfecta y positiva, y si es -1 existe relación lineal perfecta y negativa.
La función de autocorrelación simple es la representación de ρk frente a k. 
El coeficiente de autocorrelación de orden 0 es, por definición, 1. Por eso no se le incluye explı́citamente en la      función de autocorrelación. 
Es una función simétrica . Por ello, en el correlograma se representa la función de autocorrelación solamente para los valores positivos del retardo k.
Se denomina autocorrelación parcial de orden k, Φ kk , a la correlación entre dos variables aleatorias del proceso estocástico distanciadas k instantes de tiempo, pero sin considerar la existencia de las variables aleatorias intermedias (eliminando su influencia).
La función de autocorrelación parcial es la representación de Φ kk frente a k.
Un proceso es ergódico cuando conforme k se hace más grande la autocorrelación, ρk , se hace más pequeña. 
Cuando valores de la serie temporal alejados en el tiempo están muy correlacionados, es decir, cuando ρk se mantiene en unas cotas elevadas para un k grande, sucede que al aumentar el tamaño de la muestra se añade poca información nueva. La consecuencia es que los estimadores obtenidos no son consistentes, ya que el aumento del tamaño de la muestra no tendrá una especial utilidad, puesto que se deberá calcular un mayor número de covarianzas para caracterizar el proceso.

Cuando estamos ante un proceso estacionario y ergódico, todo el problema de inferencia se simplifica de forma considerable.
Nuestro objetivo al analizar una serie temporal es estimar el proceso estocástico que la genera y para ello debemos partir del supuesto de que dicho proceso estocástico es estacionario y ergódico.



### Modelo lineal general

La estructura de dependencia temporal de un proceso estocástico está recogida en las funciones de autocorrelación simple y de autocorrelación parcial. Se trata de utilizar la información de estas funciones para extraer un patrón sistemático y, a partir de éste, un modelo que reproduzca el comportamiento de la serie y se pueda utilizar para predecir.
El modelo se descompone en dos partes. Una que recoge el patrón de regularidad, o parte sistemática, y otra parte puramente aleatoria en la que sus valores no tienen ninguna relación entre sı́.
El problema es formular la parte sistemática de tal manera que el elemento residual sea un ruido blanco. El ruido blanco es el proceso estocástico más sencillo: de media cero, varianza constante y covarianzas nulas. Es un proceso puramente aleatorio.
Las condiciones generales que ha de cumplir el proceso son:
    a) Que el proceso sea no anticipante, es decir, que el presente no venga determinado por el futuro,
    b) Que el proceso sea invertible, es decir, que el presente dependa de forma convergente de su propio pasado, lo que
       implica que los coeficientes de los retardos tiendan a cero cuanto más alejados del presente. Esta condición se 
       cumple si los parámetros del modelo son finitos.
                   
El modelo lineal general admite tres representaciones:
    a) Modelos autorregresivos AR(p),
    b) Modelos de medias móviles M A(q),
    c) Modelos autorregresivos de medias móviles ARMA (p, q).

### Modelo autorregresivo AR(p)

   Xt = φ i X t−p + a t
Un proceso autorregresivo es un proceso en el que la variable Xt  se obtiene efectuando una regresión sobre valores pasados de la misma.
El caso más común es AR ( 1 ): X t = φ 1 X t − 1 + a t. En este caso, para que el proceso sea invertible ha de darse que φ sea menor que 1.
Un proceso autorregresivo AR(p) representado por
    X t = φ 1 X t − 1 + φ 2 X t − 2 + ... + φ p X t − p + a t 
es estacionario si las raíces de la ecuación
    X p − φ 1 X p−1 − φ 2 X p − 2 − ... − φ p − 1 X − φ p  = 0 
son todas inferiores a uno en módulo.

Características:
    - La función de autocorrelación simple de un modelo autorregresivo tiende a cero rápidamente, exponencialmente, 
    - La función de autocorrelación parcial de un modelo autorregresivo se hace cero en el orden del modelo (p),

### Modelo de medias móviles MA(q)

   X t = a t − θ q a t − q 
Un proceso de medias móviles de orden q es un proceso en el que la variable Xt se obtiene como un promedio de variables de ruido blanco (ai ), siendo los θi sus coeficientes de ponderación.
Características:
    - Todos los procesos de medias móviles son procesos estacionarios,
    - Existen 2q procesos de medias móviles de orden q que poseen la misma función de autocorrelación, pero solo uno de
      ellos es invertible. De esta manera si sólo consideramos procesos invertibles la función de autocorrelación 
      determina unívocamente un proceso,
    - La función de autocorrelación simple de un modelo de medias móviles se hace cero en el orden del modelo (q) y 
      caracteriza los procesos de medias móviles,
    - La función de autocorrelación parcial de un modelo de medias móviles tiende a cero rápidamente.


### Modelo autorregresivo de medias móviles ARMA(p,q)

Los modelos autorregresivos de medias móviles, ARMA(p,q), son la suma de un proceso autorregresivo de orden p y uno de medias móviles de orden q.
Las funciones de autocorrelación simple y parcial de un proceso ARMA también son la suma de las correspondientes a un proceso MA y a otro AR.
Características:
    - La función de autocorrelación simple de un proceso ARMA en cuanto supera el orden de la parte MA, q, se comporta
      como si solo hubiera parte AR.
    - La función de autocorrelación parcial se comporta como si sólo hubiera parte MA en cuanto superamos el orden de la
      parte AR, p.
Estas características de las funciones de autocorrelación dificultan la identificación del proceso a través de las mismas, de manera que no es posible identificar p y q al mismo tiempo. En un primer paso debemos identificar un proceso AR (o un MA) y, tras ajustar la serie, identificar en los residuos un MA (o un AR).


### Modelo autorregresivo integrado de medias móviles ARIMA(p,d,q)

Estos modelos incorporan la diferenciación en sus parámetros. Así, d es el orden de integración de la serie, es decir, el número de diferencias que hay que tomar a la serie para que sea estacionaria.

### Modelo estacional autorregresivo integrado de medias móviles SARIMAX (p,d,q) (P,D,Q)m

Extensión del modelo ARIMA que contempla la estacionalidad. Añade cuatro nuevos parámetros: P ,D y Q para especificar la autoregresión (AR), la diferenciación (I) y las medias móviles referidos a la estacionalidad, y m para definir el período de la estacionalidad.

### Determinación automatizada de los parámetros del modelo ARIMA/SARIMAX

Python no ofrece una manera automatizada de fijar los parámetros de un modelo SARIMAX. En este proyecto se aporta una solución para resolver esta tarea.
A partir de la fijación de una horquilla de valores para los parámetros (en este caso, entre 0 y 2) y de la determinación del período de estacionalidad (7) se obtienen todas las combinaciones posibles de los parámetros para entrenar los modelos.
Finalmente éstos se evalúan según el valor AIC (Akaike Information Criterion) obtenido. El valor AIC mide cómo se ajusta un modelo a los datos teniendo en cuenta toda la complejidad del mismo. Si dos modelos ajustan igual de bien, el valor AIC será alto si el modelo utiliza muchas features y bajo en caso contrario. Éste último caso es el que interesa.


