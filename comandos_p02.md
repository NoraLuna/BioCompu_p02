Comandos de git practica02
Equipo BioCompu
Integrante 1: Gúzman Favila Gabriela
Integrante 2: Hernández Luna Nora Hilda
Integrante 3: Rosas Paz Miguel Ángel 

Parte I.
 mkdir bioCompu_p02
 mkdir data && mkdir filtered && mkdir raw_data && mkdir meta && mkdir scripts && mkdir figures && mkdir archive
 mv filtered /home/genomica_2020-2/bioCompu_p02/data 
 mv raw_data /home/genomica_2020-2/bioCompu_p02/data 
Parte III
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
 #gaby g
