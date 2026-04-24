# Laboratorio 4 procesamiento digital
# Señales electromiográficas EMG

## Docente:
-Carolina Corredor
## Integrantes: 

-Liseth Yuliana Clavijo Mesa

-Adriana Valentina Alarcon Ramirez 

# Introduccion :

La evaluación de la actividad muscular es fundamental en áreas como la ingeniería biomédica, la rehabilitación y el deporte. Una de las técnicas más utilizadas para este propósito es la electromiografía (EMG), la cual permite registrar la actividad eléctrica generada por los músculos durante la contracción. A través de esta herramienta, es posible analizar el comportamiento muscular en diferentes condiciones fisiológicas, incluyendo la aparición de la fatiga.

La fatiga muscular es un fenómeno que implica la disminución progresiva de la capacidad del músculo para generar fuerza o mantener una contracción sostenida. Este proceso está asociado a cambios fisiológicos y metabólicos que afectan directamente las características de la señal electromiográfica. En particular, el análisis en el dominio de la frecuencia permite identificar variaciones en parámetros como la frecuencia media y la frecuencia mediana, los cuales tienden a disminuir a medida que el músculo se fatiga.

En este contexto, el procesamiento digital de señales juega un papel clave, ya que permite filtrar, segmentar y analizar la información contenida en las señales EMG. El uso de herramientas como la Transformada Rápida de Fourier (FFT) facilita la observación del contenido espectral de la señal y su evolución durante contracciones musculares repetidas.

La presente práctica de laboratorio tiene como finalidad analizar señales electromiográficas, tanto emuladas como reales, con el objetivo de identificar cambios en sus características frecuenciales asociados a la fatiga muscular. Esto permite comprender la utilidad del análisis espectral como herramienta para la evaluación objetiva del estado muscular en diferentes aplicaciones biomédicas.

# Marco teorico 

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/895c3f22-0065-4484-b5fb-e7bf6f1b40c0" />


La electromiografía (EMG) es una técnica utilizada para registrar la actividad eléctrica generada por los músculos durante la contracción. Esta señal es el resultado de la suma de los potenciales de acción de las unidades motoras activas y puede ser medida mediante electrodos de superficie colocados sobre la piel. La EMG de superficie (sEMG) permite evaluar de forma no invasiva el comportamiento muscular en distintas condiciones fisiológicas.

La señal electromiográfica es de naturaleza aleatoria y no estacionaria, con un contenido frecuencial que generalmente se encuentra entre 20 Hz y 450 Hz. Debido a esto, es necesario aplicar técnicas de procesamiento digital de señales, como el filtrado pasa banda, para eliminar ruido y artefactos, incluyendo interferencias electromagnéticas y componentes de baja frecuencia asociadas al movimiento.

Uno de los fenómenos más relevantes en el análisis de señales EMG es la fatiga muscular, definida como la disminución de la capacidad del músculo para generar fuerza o mantener una contracción sostenida. Desde el punto de vista fisiológico, la fatiga está asociada a factores como la acumulación de metabolitos (como el lactato), la disminución del ATP y cambios en la conducción de las fibras musculares.

El análisis de la fatiga muscular puede realizarse en el dominio del tiempo o en el dominio de la frecuencia. En este laboratorio, el enfoque principal es el análisis frecuencial, donde se emplean parámetros como:

Frecuencia media (Mean Frequency, MNF): promedio ponderado del espectro de frecuencias.
Frecuencia mediana (Median Frequency, MDF): frecuencia que divide el espectro en dos partes de igual energía.

Durante la fatiga muscular, se observa un desplazamiento del espectro de frecuencias hacia valores más bajos, lo que implica una disminución tanto de la frecuencia media como de la mediana. Este fenómeno se relaciona con la reducción en la velocidad de conducción de las fibras musculares y cambios en la sincronización de las unidades motoras.

Para analizar estas características, se utiliza la Transformada Rápida de Fourier (FFT), una herramienta matemática que permite convertir una señal del dominio del tiempo al dominio de la frecuencia, facilitando la identificación de sus componentes espectrales. Este análisis permite observar cómo evoluciona el contenido frecuencial de la señal a medida que el músculo se fatiga.

El uso de técnicas espectrales en señales EMG tiene aplicaciones importantes en áreas como la rehabilitación, el deporte y la ingeniería biomédica, ya que permite evaluar el estado muscular de forma objetiva, no invasiva y en tiempo real.

######¿Cómo se realiza?


<img width="305" height="265" alt="image" src="https://github.com/user-attachments/assets/17bf1caa-9a5b-47a7-8a54-ae878c301524" />



La electromiografía se realiza en dos etapas:

Electroneurografía o neuroconducción: se colocan pequeños sensores sobre la piel para evaluar determinados músculos o trayectos de nervios. Luego, se aplican pequeños estímulos eléctricos que generan actividad en esos nervios y músculos, la cual es captada por el equipo. Esta etapa puede causar una sensación similar a ligeros golpecitos, pero resulta tolerable.


Electromiografía: se inserta un electrodo en forma de aguja a través de la piel hasta alcanzar el músculo, con el fin de evaluar directamente su actividad. Durante el examen se solicita realizar algunos movimientos mientras el electrodo registra las señales. En esta etapa se percibe un dolor tipo piquete al insertar la aguja y cierta molestia durante el procedimiento, aunque de forma tolerable.
Este examen es realizado por el médico y suele estar disponible tanto en los hospitales públicos como en las clínicas privadas.

## Parte A - captura de la señal emulada.

A. Configurara el generador de señales biologicas en modo EMG, simulando aproximadamente cinco contraccionesmusculares voluntarias.

B. Adquirir y almacenar la señal generada oara su posterior análisis.

Para este paso se simulo una señal EMG con una Fs = 1 Hz y un Vpp = 5V, la señal descargada del simulador tiene 20000 muestras que van de 0 a 5 segundos y entre una muestra y la otra tiene 0.00025 segundos.

```python

import pandas as pd
import matplotlib.pyplot as plt

#Cargar archivo CSV
df=pd.read_csv('/content/drive/MyDrive/senal_adquirida 1HZ.csv')

# Ver las primeras filas
print(df.head())

# Extraer columnas
tiempo=df['Tiempo(s)']
voltaje=df['Voltaje(V)']

# Calcular frecuencia de muestreo
dt=tiempo[1]-tiempo[0]
fs=1/dt
print("\nFrecuencia de muestreo:", fs, "Hz")

# Graficar señal completa
plt.figure(figsize=(12,4))
plt.plot(tiempo, voltaje)
plt.xlabel('Tiempo (s)')
plt.ylabel('Voltaje (V)')
plt.title('Señal EMG adquirida')
plt.grid(True)
plt.show()

   Tiempo(s)  Voltaje(V)
0    0.00000    1.345282
1    0.00025    1.346248
2    0.00050    1.346248
3    0.00075    1.351079
4    0.00100    1.335298

```
<img width="995" height="381" alt="image" src="https://github.com/user-attachments/assets/9b3d2176-e1af-4197-8d95-fcebb63b2fa6" />

C. segmentar la señal obtenida en las cinco contracciones simuladas.

# Segmentación de las 5 contracciones

```python
c1 = df[(tiempo >= 0) & (tiempo < 1)]
c2 = df[(tiempo >= 1) & (tiempo < 2)]
c3 = df[(tiempo >= 2) & (tiempo < 3)]
c4 = df[(tiempo >= 3) & (tiempo < 4)]
c5 = df[(tiempo >= 4) & (tiempo < 5)]
contracciones = [c1, c2, c3, c4, c5]

fig, axs = plt.subplots(5, 1, figsize=(12,10))

axs[0].plot(c1['Tiempo(s)'], c1['Voltaje(V)'])
axs[0].set_title('Contracción 1')
axs[0].grid(True)

axs[1].plot(c2['Tiempo(s)'], c2['Voltaje(V)'])
axs[1].set_title('Contracción 2')
axs[1].grid(True)

axs[2].plot(c3['Tiempo(s)'], c3['Voltaje(V)'])
axs[2].set_title('Contracción 3')
axs[2].grid(True)

axs[3].plot(c4['Tiempo(s)'], c4['Voltaje(V)'])
axs[3].set_title('Contracción 4')
axs[3].grid(True)

axs[4].plot(c5['Tiempo(s)'], c5['Voltaje(V)'])
axs[4].set_title('Contracción 5')
axs[4].grid(True)

plt.tight_layout()
plt.show()

```

<img width="1187" height="394" alt="image" src="https://github.com/user-attachments/assets/73c220c4-cb99-45d5-9e67-b3125efceb88" />
<img width="1182" height="402" alt="image" src="https://github.com/user-attachments/assets/df163261-f761-48e2-801b-59c6b451b0cd" />
<img width="1183" height="188" alt="image" src="https://github.com/user-attachments/assets/713d538e-278e-48e4-90c9-075ffb78d03a" />

D. Calcular para cada contracción calcular la frecuancia media y frecuencia mediana.

Para cada contracción se debe obtener la FFT y luego realizar el calculo aritmetico.
```python
import numpy as np
from scipy.fft import fft, fftfreq
dt=tiempo.iloc[1]-tiempo.iloc[0]
fs=1/dt
contracciones=[c1, c2, c3, c4, c5]
frecuencia_media=[]
frecuencia_mediana=[]
for i, c in enumerate(contracciones):
    señal=c['Voltaje(V)'].values
    señal=señal - np.mean(señal)
    N=len(señal)

    Y=fft(señal)
    freqs=fftfreq(N, d=1/fs)

    freqs=freqs[:N//2]
    potencia=np.abs(Y[:N//2])**2
    freqs=freqs[1:]
    potencia=potencia[1:]
    mask=(freqs>=5) & (freqs<=250)
    freqs=freqs[mask]
    potencia=potencia[mask]

    f_media=np.sum(freqs * potencia) / np.sum(potencia)
    potencia_acum=np.cumsum(potencia)
    mitad=potencia_acum[-1] / 2
    idx=np.where(potencia_acum >= mitad)[0][0]
    f_mediana=freqs[idx]

    frecuencia_media.append(f_media)
    frecuencia_mediana.append(f_mediana)

    print(f'Contracción {i+1}')
    print(f'Frecuencia media:{f_media:.2f} Hz')
    print(f'Frecuencia mediana: {f_mediana:.2f} Hz')
    print(' ')

Contracción 1
Frecuencia media: 41.16 Hz
Frecuencia mediana: 17.00 Hz
---------------------------
Contracción 2
Frecuencia media: 41.04 Hz
Frecuencia mediana: 17.00 Hz
---------------------------
Contracción 3
Frecuencia media: 40.89 Hz
Frecuencia mediana: 17.00 Hz
---------------------------
Contracción 4
Frecuencia media: 40.90 Hz
Frecuencia mediana: 17.00 Hz
---------------------------
Contracción 5
Frecuencia media: 40.88 Hz
Frecuencia mediana: 17.00 Hz
---------------------------
```

Para cada uno de las contracciones segmentadas se calculo la frecuencia media y mediana a partir del espectro de potencia obteido mediante la FFT con el fin de caracterizar la distribución de enegíade la señal en el dominio de la frecuancia, la frecuencia media representa el promedio ponderado de las frecuencias presentes, considerando la potencia asociada a cada una, mientras que la mnediana corresponde al valor que divide el espectro en dos partes con igual contenido.


En los resultados se obtuvieron frecuencias medias al rededor de los 40 Hz y frecuencias medianas al rededor de 17 Hz, esta diferencia se debe a que 
la señal presenta mayor concentración de energía en bajas frecuencias, lo que hace que la frecuencia mediana tome valores mas pequeños,mientras que lña frecucnia media se ve mayormente influenciada por componentes de frecuencia mas altas presentes en el espectro.

### Tabla de datos de frecuencias 


```python
import pandas as pd

tabla = pd.DataFrame({
    'Contracción': [1, 2, 3, 4, 5],
    'Frecuencia media (Hz)': frecuencia_media,
    'Frecuencia mediana (Hz)': frecuencia_mediana
})

print(tabla)

   Contracción  Frecuencia media (Hz)  Frecuencia mediana (Hz)
0            1              41.158523                     17.0
1            2              41.042417                     17.0
2            3              40.885795                     17.0
3            4              40.896305                     17.0
4            5              40.881622                     17.0
```

### Grafica de evolución de frecuencias 

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(8,5))

plt.plot(tabla['Contracción'], tabla['Frecuencia media (Hz)'], marker='o', label='Frecuencia media')
plt.plot(tabla['Contracción'], tabla['Frecuencia mediana (Hz)'], marker='s', label='Frecuencia mediana')

plt.xlabel('Contracción')
plt.ylabel('Frecuencia (Hz)')
plt.title('Evolución de frecuencias por contracción')

plt.grid(True)
plt.legend()

plt.show()
```

<img width="681" height="461" alt="image" src="https://github.com/user-attachments/assets/b9429600-0852-4938-b6d3-a4586137f1c2" />

La gráfica muestra que la frecuencia media y la frecuencia mediana permanecen practicamente constante a lo largo de las cinco contracciones, esto indica que no hay variaciones significativas en el contenido espectral de la señal, este comportamiento es el esperado ya que se analizo una señal simulada con caracteristicas similares en cada contracción, a diferenciad de las EMG reales, no se observa un desplazamiento hacia frecuencias bajas ya que no se evidencia fatiga muscular.

F. Analizar como varian estas frecuencias a lo largo de las comtracciones simuladas.

Se observa que tanto la frecuencia mediana como la frecuencia media se mantiene en un rango constrante a lo largo de la señal o de las contracciones, con valores aproximados a 17 HZ y 40 Hz respectivamente, no se evidencia una disminución progresiva significatia en frecuencias por lo que no se presenta un comportamiento de fatiga muscular debido a que es simulada, en las señales EMG reales si se suele evidenciar la fatiga como un desplazamiento del espectro hacia baja frecuencias, lo cual no se evidencia para esta parte A

# Parte C
## Análisis espectral mediante FFT 
a. Aplicar la Transformada Rápida de Fourier (FFT) a cada contracción de la señal EMG real. 


```python

fft_resultados = []

for i, seg in enumerate(segments):
    freqs, spectrum = compute_fft(seg, fs)

    fft_resultados.append((freqs, spectrum))

    print(f'FFT aplicada a Contracción {i+1} (N = {len(seg)})')
```

Se aplicó la Transformada Rápida de Fourier (FFT) a cada una de las contracciones obtenidas de la señal electromiográfica (EMG), con el fin de transformar la señal del dominio del tiempo al dominio de la frecuencia. Este procedimiento permitió identificar las componentes frecuenciales presentes en la señal y analizar la distribución de energía en función de la frecuencia.
Para cada segmento correspondiente a una contracción, se calculó su espectro de frecuencia, obteniendo como resultado el conjunto de frecuencias y su respectiva magnitud o potencia asociada.

b. Graficar el espectro de amplitud (frecuencia vs. magnitud) para observar cómo cambia el contenido de frecuencia. 
En las gráficas obtenidas se representa el espectro de potencia de cada contracción de la señal EMG en función de la frecuencia. El eje horizontal corresponde a la frecuencia en Hz (en escala semilogarítmica), mientras que el eje vertical representa la potencia asociada a cada componente frecuencial.

```python
plt.figure(figsize=(12,8))

for i, seg in enumerate(segments):
    freqs, spectrum = compute_fft(seg, fs)

    power = spectrum**2  # usar potencia

    plt.subplot(5,1,i+1)
    plt.semilogx(freqs, power)
    plt.title(f'Contracción {i+1}')
    plt.ylabel('Potencia')
    plt.xlim(1, 500)
    plt.grid(True, which='both')

plt.xlabel('Frecuencia (Hz)')
plt.tight_layout()
plt.show()

```

<img width="1035" height="654" alt="image" src="https://github.com/user-attachments/assets/e1eaa79f-cfbe-4c30-9404-e9746e770145" />



A partir de las gráficas se observa que, en todas las contracciones, la mayor concentración de energía se encuentra en un rango aproximado entre 20 y 100 Hz. Este comportamiento es característico de señales electromiográficas, ya que la actividad eléctrica muscular suele concentrarse en frecuencias bajas y medias. Además, en cada espectro se identifica un pico principal, el cual corresponde a la frecuencia dominante de la señal, es decir, donde se concentra la mayor potencia.

También se aprecia que a medida que aumenta la frecuencia, la potencia disminuye progresivamente, lo cual indica que las componentes de alta frecuencia tienen menor contribución en la señal.

Un aspecto importante es que los espectros de todas las contracciones presentan formas muy similares entre sí. Esto significa que la distribución de energía en frecuencia se mantiene prácticamente constante a lo largo de las diferentes contracciones. Esta similitud puede explicarse por dos razones principales: en primer lugar, la segmentación de la señal se realizó dividiéndola en partes iguales, lo cual no garantiza que cada segmento corresponda exactamente a una contracción independiente; y en segundo lugar, es posible que no exista un nivel significativo de fatiga muscular, ya que en presencia de fatiga se esperaría un desplazamiento del contenido espectral hacia frecuencias más bajas y una reducción en las componentes de alta frecuencia.

En consecuencia, las gráficas indican que la señal EMG analizada mantiene un comportamiento espectral estable, sin cambios notorios en la distribución de frecuencias entre las distintas contracciones. Esto sugiere que la actividad muscular registrada no presenta variaciones significativas en términos de fatiga durante el periodo de análisis.


c. Comparar los espectros de las primeras contracciones con los de las últimas. 

```python
freqs1, spec1 = compute_fft(segments[0], fs)
freqs5, spec5 = compute_fft(segments[-1], fs)

plt.figure()
plt.semilogx(freqs1, spec1**2, label='Inicio')
plt.semilogx(freqs5, spec5**2, label='Final')

plt.title('Inicio vs Final (Fatiga)')
plt.xlabel('Frecuencia (Hz)')
plt.ylabel('Potencia')
plt.xlim(1, 500)
plt.legend()
plt.grid(True, which='both')
plt.show()

```
<img width="516" height="370" alt="image" src="https://github.com/user-attachments/assets/15aabac4-e9ee-4c45-8936-1322431a4953" />

Para evaluar posibles cambios en el contenido frecuencial de la señal EMG, se realizó una comparación entre el espectro correspondiente a la primera contracción (inicio) y el de la última contracción (final), como se muestra en la figura.

En la gráfica se observa que ambos espectros presentan una distribución de potencia muy similar, con la mayor concentración de energía en el rango de frecuencias bajas y medias (aproximadamente entre 20 y 100 Hz). El pico espectral principal aparece en una frecuencia cercana en ambas señales, lo que indica que la frecuencia dominante del músculo se mantiene prácticamente constante entre el inicio y el final del registro.

Sin embargo, se aprecian pequeñas variaciones en la amplitud de algunas componentes, especialmente en el rango de frecuencias medias y altas, donde el espectro final presenta ligeras diferencias respecto al inicial. Estas variaciones pueden estar asociadas a cambios en la activación muscular o a ruido en la señal.

En general, la alta similitud entre ambos espectros sugiere que no se produjo un cambio significativo en el contenido frecuencial de la señal a lo largo del tiempo. En condiciones de fatiga muscular, se esperaría observar una disminución de las componentes de alta frecuencia y un desplazamiento del espectro hacia frecuencias más bajas; sin embargo, este comportamiento no es claramente evidente en la gráfica obtenida.

d. Identificar la reducción del contenido de alta frecuencia asociada con la fatiga muscular.  

```python
high_energy = []

for seg in segments:
    freqs, spectrum = compute_fft(seg, fs)
    power = spectrum**2

    mask = freqs > 100  # altas frecuencias
    energy = np.sum(power[mask])

    high_energy.append(energy)

plt.figure()
plt.plot(range(1,6), high_energy, marker='o')
plt.title('Energía en altas frecuencias')
plt.xlabel('Contracción')
plt.ylabel('Energía')
plt.grid()
plt.show()

```

<img width="541" height="384" alt="image" src="https://github.com/user-attachments/assets/5be97c80-1500-47c2-8ad0-676089572621" />


Con el fin de analizar la presencia de fatiga muscular, se evaluó la energía contenida en las altas frecuencias de la señal EMG para cada una de las contracciones, como se muestra en la figura.

En la gráfica se observa que la energía en altas frecuencias no presenta una disminución progresiva a lo largo de las contracciones. Inicialmente, se evidencia una leve reducción desde la primera hasta la tercera contracción; sin embargo, posteriormente la energía aumenta nuevamente en las contracciones cuarta y quinta.

Este comportamiento no corresponde al patrón típico de fatiga muscular, en el cual se espera una disminución sostenida del contenido de altas frecuencias debido a cambios fisiológicos en la conducción de las fibras musculares. En condiciones de fatiga, la señal EMG tiende a concentrar su energía en frecuencias más bajas, reduciendo progresivamente las componentes de alta frecuencia.

La ausencia de una tendencia decreciente clara en la gráfica sugiere que no se presentó un nivel significativo de fatiga muscular durante el experimento. Asimismo, las variaciones observadas pueden estar influenciadas por factores como la segmentación de la señal, el ruido o pequeñas diferencias en la activación muscular entre contracciones.

e. Calcular y discutir el desplazamiento del pico espectral y su relación con el esfuerzo sostenido. 

```python

for seg in segments:
    freqs, spectrum = compute_fft(seg, fs)
    power = spectrum**2

    peak = freqs[np.argmax(power)]
    peak_freqs.append(peak)

plt.figure()
plt.plot(range(1,6), peak_freqs, marker='s')
plt.title('Desplazamiento del pico espectral')
plt.xlabel('Contracción')
plt.ylabel('Frecuencia (Hz)')
plt.grid()
plt.show()

```



f. Redactar conclusiones sobre el uso del análisis espectral como herramienta diagnóstica en electromiografía.




# Referencias 
-Tuasaúde. (s.f.). Electromiografía: qué es, para qué sirve y cómo se realiza. Recuperado el 23 de abril de 2026, de https://www.tuasaude.com/es/electromiografia/


