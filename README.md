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



# Referencias 
-Tuasaúde. (s.f.). Electromiografía: qué es, para qué sirve y cómo se realiza. Recuperado el 23 de abril de 2026, de https://www.tuasaude.com/es/electromiografia/


