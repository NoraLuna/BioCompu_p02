#  Comandos de git practica02
## Equipo BioCompu
## Integrante 1: Gúzman Favila Gabriela
## Integrante 2: Hernández Luna Nora Hilda
## Integrante 3: Rosas Paz Miguel Ángel 

### Parte I.
mkdir bioCompu_p02

mkdir data && mkdir filtered && mkdir raw_data && mkdir meta && mkdir scripts && mkdir figures && mkdir archive

mv filtered /home/genomica_2020-2/bioCompu_p02/data 

mv raw_data /home/genomica_2020-2/bioCompu_p02/data 

### Parte III. 
ln -s /ERR486827_2.fastq.gz /mnt/c/Users/Gabriela/Downloads/genomica_2020/genomica_2020-2-master/BioCompu_p02/data/filtered/ERR486827_2.fastq.gz 

ln -s /ERR486827_1.fastq.gz /mnt/c/Users/Grabiela/Downloads/genomica_2020/genomica_2020-2-master/BioCompu_p02/data/filtered/ERR486827_1.fastq.gz 

gunzip -c ERR486827_1.fastq.gz | awk '{if(NR%4==1) {printf(">%s\n",substr($0,2));} else if(NR%4==2) print;}' >file.fa  

gunzip -c ERR486827_2.fastq.gz | awk '{if(NR%4==1) {printf(">%s\n",substr($0,2));} else if(NR%4==2) print;}' >file2.fa

grep -c ERR4868 file.fa # 398824

grep -c ERR4868 file2.fa # 398824  

awk 'NR%2==0{print length "."}' file.fa

awk 'NR%2==0{print length "."}' file.fa >longitudes1.csv

awk 'NR%2==0{print length "."}' file_2.fa

awk 'NR%2==0{print length "."}' file.fa >longitudes_2.csv

ln -s /sequence.gff3 /home/genomica_2020-2/nueva/bioCompu_p02/data/filtered/sequence.gff3

**Respuesta de la pregunta 2:** Ambos archivos tienen la misma cantidad de secuencias con 398824 cada una.

**Respuesta de la pregunta 3:** 

AGCATGTTAGATTA  GATAGCTGTGCTA

      TTAGATAAAGGATA CTG

6M1I1M2D4M1D3M

14M de CIGAR

### Parte IV.

mkdir bin

unzip fastqc_v0.11.0.zip

chmod+x fastqc

ln -s /ERR486827_2.fastq.gz /mnt/c/Users/Gabriela/Downloads/genomica_2020/genomica_2020-2-master/BioCompu_p02/data/filtered/ERR486827_2.fastq.gz 

ln -s /ERR486827_1.fastq.gz /mnt/c/Users/Grabiela/Downloads/genomica_2020/genomica_2020-2-master/BioCompu_p02/data/filtered/ERR486827_1.fastq.gz 

touch delay.sh

vi delay.sh  

|#!/bin/bash                     |


|fastqc file_1.fastq file_2.fastq|

./fastqc_run.sh

**Respuesta de la pregunta 3:** Análisis de gráficas FastqC

**Archivo 1:** La calidad de la secuencia en general es buena, con peores valores en las primeras posiciones, pero siempre cayendo en la región de calidad verde. 

La gráfica de calidad por mosaico no muestras celdas con mala calidad. La media de la calidad es 37 y la mayoría de las secuencias se encuentran en este valor.

Así pues, la cantidad de GC de la secuencia se acerca mucho a la proporción teórica y el contenido de N por base prácticamente nulo. 

Todas las secuencias presentan una longitud de 150 pares de bases, no hay secuencias duplicadas o sobre representadas. 

En conjunto, estos datos muestras que esta secuenciación tiene una muy buena calidad. 

**Archivo 2:** Las calidades por base son buenas, siempre entrando en un valor entre 28-40. No obstante, la calidad por posición presenta mayor variación que en la secuencia anterior.

La gráfica de mosaico no muestra celdas con mala calidad. La media de la calidad es 37, con la mayoría de las secuenicas en este valor. 

La cantidad de GC observada se acerca a la esperada y el contenido de N es casi nulo. Todas las secuenicas presentan longitud de 150 pb, no hay secuencias duplicadas o sobre representadas.

Por lo anterior, podemos decir que la calidad de estas secuencias es buena. 

**Respuesta de la pregunta 4:** Cobertura del genoma = (797648*150)/580000 = 206.288

### Parte V.

mv Virgibacillus_1.html /home/genomica_2020-2/bioCompu_p02/data/raw_data

mv Virgibacillus_2.html /home/genomica_2020-2/bioCompu_p02/data/raw_data

chmod+x fastqc

ln -s /Virgibacillus_1.fastq.gz /mnt/c/Users/Gabriela/Downloads/genomica_2020/genomica_2020-2-master/BioCompu_p02/data/filtered/Virgibacillus_1.fastq.gz #teóricos

ln -s /Virgibacillus_2.fastq.gz /mnt/c/Users/Grabiela/Downloads/genomica_2020/genomica_2020-2-master/BioCompu_p02/data/filtered/Virgibacillus_2.fastq.gz #teóricos

touch fastqc2_run.sh

vi fastqc2_run.sh

|#!/bin/bash                     |


|fastqc fileV_1.fastq fileV_2.fastq|

./fastqc_run.sh

**Respuesta de la pregunta 2:** La tecnología utilizada fue Illumina/ Sanger. En esta tecnología, se utilizan nucleótidos terminadores

marcados con moléculas fluorescentes al igual que en la Secuenciación de Sanger. Además de tener la capacidad

de realizar millones de secuencias en cada corrida, la diferencia con el método convencional es la posibilidad 

de eliminar la fluorescencia una vez obtenida la imagen, y desbloquear carbono 3’ de modo que pueda aceptar una nueva

base para continuar la reacción de secuenciación, haciendo que la incorporación de un

nucleótido terminador sea reversible.

**Respuesta de la pregunta 3:** Cobertura del genoma = ( 9108064*150)/4561556 = 299.5051

**Respuesta de la pregunta 4:**

**Respuesta de la pregunta 5:** 

**Archivo1:** Las calidades por base son buenas en la mayoría de la secuencias, pero decaen en el extremo 3', llegando hasta la región roja (mala calidad). 

La media de la calidad es de 36, pero se observa un pico en el valor de calidad 18-20. Si bien, no muchas secuencias caen en el valor anterior, estas podrían representar el extremo 3'.

la cantidad de GC observada se acerca mucho a la esperada, pero la distribución en la gráfica es ligeramente distinta em ambas, lo que podría deberse a las lecturas de mala calidad en 3'. 

No obstante, la cantidad de N es prácticamente nula. 

**Archivo2:** Al igual que en el archivo 1, las calidades por base son buenas en la mayoría de la secuencias, pero decaen en el extremo 3', particularmente a partir de 105- 109 pb, llegando hasta la región roja (mala calidad). 

La media de la calidad es de 36, pero se observa un pico en el valor de calidad 18-20. Si bien, no muchas secuencias caen en el valor anterior, estas podrían representar el extremo 3'.

la cantidad de GC observada se acerca mucho a la esperada, pero la distribución en la gráfica es ligeramente distinta em ambas, lo que podría deberse a las lecturas de mala calidad en 3'. 

No obstante, la cantidad de N es prácticamente nula. 

**Respuesta de la pregunta 6:** 30 phred

**Respuesta de la pregunta 7:** Debido a que nuestras secuencias se encuentran con mala calidad hacia el extremo 3', pensamos que lo más conveniente en este caso es cortar las secuencias entre las 105 y109 pb, 

que es el intervalo de pb donde se cmienza a presentar la baja calidad de las secuencias. Para ello, Trimmomatic podría servir como software base, pues entre sus propiedades se encuentra la capacidad

de remover adaptadores y de cortar secuencias.
