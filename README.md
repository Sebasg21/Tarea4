# Universidad de Costa Rica

### Facultad de Ingeniería

### Escuela de Ingeniería Eléctrica

#### IE0405 - Modelos Probabilísticos de Señales y Sistemas

#### Sebastián Gómez Chaves; B42866
#### Grupo 02

# Tarea 4

Se debe trabajar con una lista de bits asignados en el archivo "bits10k.csv" por lo que se necesita de la librería numpy para realizar la lectura del archivo. Seguidamente una vez con el arreglo correspondietne de los bits, se procede a cummplir con los requerimientos especificados.

1. Crear un esquema de modulación BPSK para los bits presentados.

Inicialmente es necesario determinar la frecuencia de trabajo, que en este caso se asignó un valor de 5000 Hz, con lo que se encuentra el periodo de la onda y se define el numero de puntos de muestreo por periodo. Seguidamente se crea la forma de onda de la portadora, una señal senoidal. Para el proceso de la modulación se asigna un bucle "for" para recorrer todos los bits del arreglo obtenido del archvio "bits10k" donde se determina que si se tiene un 1 se asigna una señal "sinus" a la señal modulada y de ser un 0 se asigna "-sinus", de tal forma que al imprimir la señal modulada para los primeros bits se muestra en la imagen "ModulacionBPSK".

2. Calcular la potencia promedio de la señal modulada generada

Para determinar la potencia promedio de la señal modulada generada se trabaja con la potencia instantanea, que es obtenida al elevar al cuadrado la señal modulada, seguidamente por medio de la integral de la potencia encontrada dividida entre el numero de bits por el periodo de cada simbolo se determina el valor de la potencia promedio. Se obtuvo un valor de 0.49 W.

3. Simular un canal ruidoso del tipo AWGN (ruido aditivo blanco gaussiano) con una relación señal a ruido (SNR) desde -2 hasta 3 dB

Al simular un canal ruidoso primeramente se debe escoger un valor de la señal de ruido (SNR) entre el rango de valores específicos brindados, con lo que se procede a calcular la potencia del ruido según la potencia de la señal. Se determina la desviacion estandar del ruido como la raíz cuadrada de la potencia del mismo. Con el valor encontrado se procede a crear el ruido con valores random en el ambito asignado por la desviación estandar "sigma", que se debe sumar a la señal para poder ser visualizada la simulación del canal ruidoso. Se muestra la gráfica con ruido en la imagen "Canal ruidoso".

4. Graficar la densidad espectral de potencia de la señal con el método de Welch (SciPy), antes y después del canal ruidoso

Para este segmento se implementa "signal.welch()" que es un método que estima la densidad espectral de potencia de una señal. Se utilizó para la señal modula y la señal con ruido, donde se obtuvieron las gráficas "Densidad antes" y "Densidad despues".

5. Demodular y decodificar la señal y hacer un conteo de la tasa de error de bits (BER, bit error rate) para cada nivel SNR.

Como se debe obtener la demodulación y decodificación para cada nivel del SNR asignado se implementan dos ciclos "for" para determinar con mas facilidad la tasa de error para cada caso.
Se inicia definiendo el vector de niveles SNR desde -2 hasta 3 dB, así como un vector para acumuar los BER y los errores de cada nivel. Se calcula la pseudo-energía de la onda original y una vez que se tienen los vectores y variables de interés definidas se impliementa el primer ciclo. Este es un procedimiento igual al implementado para el punto tres sin embargo con la condición de que recorre el vector SNR, para cada nivel por medio del segundo ciclo calcula la decodificación de la señal por detección de energía con lo que posteriormente se procede a calcular la tasa de error para cada nivel.
Es importante recalcar que el hecho de que el ruido esté producido por valores aleatorios puede generar alteraciones en los resultados al correrse en varias ocaciones, sin embargo se tiene una congruencia en los valores al determinar que para niveles de SNR cercanos a -2 se esperan más errores debido al sigma obtenido.

6. Graficar BER versus SNR

Para generar la gráfica sencillamente se debe plotear el vector BER1 qeu corresponde a la tasa de error guardada para cada nivel contra el vector SNR. Se muestra la gráfica en la imagen "BERvsSNR". 


```python

```
