## Comparación Galaxy vs línea de comando (Terminal Mac)

Se puede observar que existen diferencias entre correr en Galaxy vs línea de comando, a continuación capturas
de pantalla de los resultados obtenidos y comparaciones respectivas. 

<img width="469" height="320" alt="image" src="https://github.com/user-attachments/assets/a106e954-a47b-4949-9c22-32dd08d4067e" />

Figura 1. Línea de comando corrida en terminal Mac


### Resultados mostrados por Galaxy vs línea de comando (Terminal Mac)

<img width="346" height="229" alt="image" src="https://github.com/user-attachments/assets/f64ef437-de92-467b-8d3e-9bf484895ef9" />             

Figura 2. Resumen del reporte FastQC secuencia Forward usando Galaxy.


<img width="335" height="257" alt="image" src="https://github.com/user-attachments/assets/e597c966-a0d4-4649-a401-2e181ae0f691" />

Figura 3. Gráfico de la calidad de Secuencias por Base, secuencia Forward usando Galaxy.


<img width="346" height="229" alt="image" src="https://github.com/user-attachments/assets/fefda326-971e-4e13-9071-a7688b80d138" />

Figura 4. Resumen del reporte FastQC secuencia combinada (forward + reverse) usando Terminal de MAC.


<img width="335" height="257" alt="image" src="https://github.com/user-attachments/assets/076a2246-c3bf-4969-a407-d29cf8e63cde" />

Figura 5. Gráfico de la calidad de Secuencias por Base, secuencia combinada (forward + reverse) usando Terminal de MAC.


### Conclusiones
Los resultados obtenidos en Galaxy vs la terminal de Mac presentan diferencias
debido a que no se analizaron exactamente los mismos archivos ni bajo las
mismas condiciones de procesamiento. En Galaxy se trabajó con lecturas
paired-end separadas (forward y reverse), mientras que en la terminal se
ejecutó FastQC sobre un único archivo FASTQ comprimido y posteriormente sobre
un archivo trimmed generado localmente. Esto explica diferencias en el 
número total de secuencias y bases reportadas. En Galaxy se registraron
aproximadamente 1,1 millones de lecturas y 165,9 Mbp, mientras que en la
terminal se obtuvieron 2,2 millones de lecturas y 331,8 Mbp, evidenciando
que el archivo utilizado en la terminal contenía mayor cantidad de datos.

Adicionalmente, la visualización de calidad por base también fue diferente.
Galaxy mostró diagramas completos tipo boxpot, donde se observan medianas,
cuartiles y dispersión de calidad en cada posición de lectura. Por otro
lado, en la terminal el gráfico apareció simplificado, mostrando únicamente
una línea horizontal de calidad constante cercana a Q30. Esto puede ocurrir
cuando el archivo procesado presenta valores de calidad muy homogéneos,
cuando FastQC interpreta un formato reducido de calidad o cuando el archivo
ya fue previamente procesado mediante trimming. 

A pesar de estas diferencias visuales, ambos análisis coinciden en que las
secuencias poseen una calidad general adecuada para análisis posteriores
de ensamblaje y anotación genómica. 

