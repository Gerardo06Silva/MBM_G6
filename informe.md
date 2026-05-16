# Proyecto: Análisis de calidad, ensamblaje y caracterización genómica de Escherichia coli a partir de secuencias FASTQ  

## Integrantes
- Gerardo Silva
- Katherine Cevallos
- Johanna Montenegro P.

## Objetivo

<p align="justify">
Procesar lecturas FASTQ de Escherichia coli mediante control de calidad, depuración y ensamblaje de novo, con el fin de obtener una secuencia genómica evaluable e identificar parámetros relevantes como longitud del ensamblaje, contenido GC, cobertura y posibles regiones codificantes.
</p>

### 1. Introducción

<p align="justify">
Echerichia coli es uno de los microorganismos modelo más utilizados en biología molecular, microbiología y bioinformática debido a que posee un genoma relativamente pequeño, ampliamente caracterizado y disponible en múltiples bases de datos genómicas públicas. Además de su importancia como organismo modelo, algunas cepas de E. coli tienen relevancia clínica y biotecnológica, ya que pueden participar en procesos industriales, producción de proteínas recombinantes y estudios relacionados con resistencia antimicrobiana y evolución bacteriana (Yibar et al., 2024).
</p>
<p align="justify">
El desarrollo de tecnologías de secuenciación masiva ha permitido generar grandes volúmenes de datos genómicos bacterianos en formatos como FASTQ, facilitantdo el análisis bioinformático de genomas completos mediante flujos de trabajo de ensamblaje y anotación en plataformas reproducibles como Galaxy (Batut et al., 2024). Actualmente, herramientas como FastQC, Trimmomatic, SPAdes, QUAST y Prokka son ampliamente utilizadas para evaluar calidad de lecturas, ensamblar genomas de novo y caracterizar regiones funcionales bacterianas. Estas herramientas permiten obtener métricas importantes como contenido GC, número de contigs, continuidad del ensamblaje y predicción de genes codificantes (Batut et al., 2024; Galaxy Training Network, 2024).
</p>
<p align="justify">
En este proyecto se trabajó con secuencias WGS (Whole Genome Sequencing) de Echerichia coli obtenidas desde el repositorio SRA del NCBI, específicamente el dataset SRR38439492. El objetivo fue procesar lecturas FASTQ mediante control de calidad, depuración y ensamblaje de novo, con el fin de obtener un ensamblaje genómico evaluable e identificar parámetros relevantes como longitud del ensamblaje, cobertura y regiones potencialmente codificantes. Este tipo de análisis constituye una base fundamental para estudios de genómica comparativa, evolución bacteriana y caracterización funcional de microorganismos procariotas (Schwengers et al., 2021).
</p>

### 2. Metodología 

<p align="justify">
En primer lugar, se obtuvieron las secuencias crudas en formato FASTQ desde la base de datos NCBI SRA. Estos archivos contienen las lecturas generadas por secuenciación, junto con la información de calidad de cada base. La descarga de los datos se realizó mediante herramientas como NCBI SRA y la plataforma Galaxy, obteniendo como resultado los archivos FASTQ iniciales.
</p>
<p align="justify">
Posteriormente, se realizó un control de calidad inicial utilizando FastQC. Se revisaron aspectos como la calidad de las bases, la presencia de adaptadores, el contenido GC, la longitud de las secuencias y posibles duplicaciones. Con esta información se pudo decidir si las lecturas eran adecuadas o si necesitaban una limpieza previa.  
</p>
<p align="justify">
Cuando las lecturas no cumplían completamente con los criterios de calidad, se aplicó un proceso de limpieza y filtrado usando herramientas como Trimmomatic y fastp. Este paso permitió eliminar fragmentos de baja calidad, adaptadores y secuencias muy cortas que podrían afectar los resultados posteriores. Como resultado, se obtuvieron lecturas más limpias y confiables para el ensamblaje del genoma.  
</p>
<p align="justify">
Una vez obtenidas las lecturas limpias, se procedió al ensamblaje del genoma mediante la herramienta Shovill. Esta etapa consistió en unir las lecturas que compartían regiones similares para formar secuencias más largas llamadas contigs. Estos contigs representan fragmentos reconstruidos del genoma de E. coli y constituyen la base para los análisis siguientes.  
</p>
<p align="justify">
Después del ensamblaje, se evaluó su calidad utilizando QUAST. En esta fase se analizaron métricas como el valor N50, la longitud total del ensamblaje, el número de contigs y el porcentaje de GC. Estos indicadores permitieron determinar si el ensamblaje era adecuado y si los resultados obtenidos eran coherentes con lo esperado para un genoma bacteriano.  
</p>
<p align="justify">
Si el ensamblaje no cumplía con los criterios esperados, se regresaba a revisar la calidad de las lecturas, los parámetros de limpieza y las condiciones del ensamblaje.  Cuando el ensamblaje fue considerado aceptable, se realizó la anotación del genoma utilizando Prokka. Esta herramienta permitió identificar los principales elementos genéticos presentes en el genoma ensamblado, como regiones codificantes, genes, CDS, RNA y tRNA.  
</p>
Finalmente, se obtuvo un genoma de E. coli ensamblado, evaluado y anotado.  
<br>
<p align="center">
<img width="297" height="419" alt="image" src="https://github.com/user-attachments/assets/67ca0129-4e5b-4a8c-b789-fdaa4345e742" />
<br>
  Figura 1. Diagrama de flujo para el ensamblaje de secuencia de E. Coli.
</p>

### 3. Resultados

#### 3.1 Calidad de secuencias crudas.
<p align="justify">
Para evaluar la viabilidad de los datos de secuenciación obtenidos para el archivo de la secuencia cruda, se realizó un control de calidad inicial utilizando la herramienta FastQC. Los resultados muestran un perfil general de alta calidad, idóneo para procesos posteriores de ensamblaje o alineamiento, aunque se identificaron anomalías menores en la composición de las bases al inicio de las lecturas.
</p>

##### 3.1.1 Estadísticas Básicas de la Corrida
<p align="justify">
El archivo analizado contiene un total de 1,106,152 secuencias (lecturas individuales), con una longitud uniforme de 150 pb por lectura, sumando un total de 165.9 Mbp. No se registraron secuencias marcadas como de baja calidad por el secuenciador. El contenido global de GC es del 50%, un valor balanceado y esperado para este tipo de genotecas de secuenciación masiva.
</p>

##### 3.1.2 Análisis de Indicadores Exitosos.
<p align="justify">
- Calidad por base (Per base sequence quality): Este indicador muestra un comportamiento óptimo. Los puntajes de calidad Phred se mantienen consistentemente en la zona verde del gráfico (Q > 28) a lo largo de toda la extensión de los 150 pb. Al inicio, la mediana se sitúa en Q38 y asciende rápidamente hasta estabilizarse en Q44 en el cuerpo de la lectura, decayendo sutilmente a Q42 hacia el extremo 3'. Esto indica una probabilidad de error de llamada de bases extremadamente baja (menor al 0.01%).
-Distribución de calidad por secuencia (Per sequence quality scores): Confirma que la gran mayoría de las lecturas tienen un comportamiento uniforme de calidad alta, concentrándose el grueso de los datos en valores Phred superiores a Q40.
</p>

##### 3.1.3 Análisis de Alertas y Fallos.
<p align="justify">
A pesar de la robustez general en la precisión de las bases individuales, el reporte arrojó llamadas de atención en los siguientes módulos:
- Calidad por azulejo (Per tile sequence quality): El mapa de calor azul revela algunas trazas discretas en tonos verdes/amarillos aislados (por ejemplo, cerca de la posición 60-64 pb en canales específicos de celdas de flujo).
- Contenido de GC por secuencia (Per sequence GC content): La curva empírica de distribución de GC (línea magenta) se ajusta razonablemente bien a la distribución teórica normal (línea azul). Sin embargo, la alerta se dispara debido a un ligero ensanchamiento y un hombro menor hacia la izquierda de la gráfica (entre el 30% y 40% de GC).
- Contenido de bases por posición (Per base sequence content): Este módulo reporta un fallo crítico debido a las fluctuaciones severas observadas en los primeros 9 a 10 pares de bases de las lecturas. Teóricamente, las líneas de las cuatro bases (A, T, C, G) deberían correr paralelas y estables. En este caso, se aprecian picos y valles pronunciados en los extremos 5'.
</p>

#### 3.2	Calidad de secuencias recortadas (segundo corte).
<p align="justify">
Tras someter el set de datos de la secuencia despues del primer corte a un segundo proceso de curación bioinformática mediante la herramienta Trimmomatic, se evaluó la efectividad del filtrado ejecutando un tercer análisis de control de calidad con FastQC. Los resultados muestran una mejora sustancial en la homogeneidad de la composición de bases y la remoción absoluta de secuencias de adaptadores, consolidando un set de lecturas altamente confiable para las etapas posteriores de ensamblaje o alineamiento.
</p>

##### 3.2.1 Modificaciones en las Estadísticas Básicas
<p align="justify">
El proceso de limpieza modificó los parámetros estructurales de la siguiente manera:
- Total de secuencias: Se retuvieron un total de 1,087,415 lecturas agrupadas como pares válidos. Esto representa una retención de aproximadamente el 98.3% respecto al archivo original.
- Rendimiento global: La genoteca final aporta 138.8 Mbp. El contenido global de GC se mantuvo estable en un 50%.
- Longitud de secuencia (Sequence Length Distribution): A diferencia de la longitud uniforme de 150 pb observada en las secuencias crudas, este módulo ahora reporta una distribución variable que oscila entre 25 pb y 133 pb. 
</p>

##### 3.2.2 Evaluación de Módulos Corregidos y Optimizados.
<p align="justify">
-	Contenido de bases por posición (Per base sequence content): Este módulo pasó de una condición de fallo crítico a un estado completamente óptimo. Las fluctuaciones severas que superaban el 10% de divergencia en los primeros 10 pb fueron eliminadas por completo. Ahora, las líneas de las cuatro bases (A, T, C, G) corren paralelas, estables y balanceadas de forma uniforme en un valor cercano al 25% desde la primera base hasta el final de la lectura. 
-	Calidad por base (Per base sequence quality): La calidad individual se mantiene en rangos de excelencia. Los puntajes Phred se estabilizan uniformemente en la zona verde (Q > 28), mostrando una mediana plana de Q44 a lo largo de casi toda la extensión de las lecturas, con una dispersión mínima en los percentiles inferiores que apenas roza Q40 en las últimas posiciones.
-	Contenido de adaptadores (Adapter Content): El indicador cambió a un estado completamente limpio. El remanente de secuencias de vectores Illumina detectado en el extremo 3' de la corrida cruda fue removido al 100%.
</p>

##### 3.2.3 Persistencia de Alertas y Anomalías Locales.
<p align="justify">
A pesar de la optimización general, el reporte conserva llamadas de atención en dos módulos específicos que responden a características intrínsecas de la corrida física y de la muestra:
-	Calidad por azulejo (Per tile sequence quality): Este indicador pasó de una alerta a un fallo. El mapa de calor revela manchas densas y localizadas en tonalidades verdes, amarillas y rojas (por ejemplo, en los azulejos de la serie 21202 y 21102 entre las posiciones 37 pb y 55 pb).
-	Contenido de GC por secuencia (Per sequence GC content): La alerta persiste debido a que la distribución empírica de GC continúa mostrando un ligero ensanchamiento en el flanco izquierdo (bajas concentraciones de GC, entre el 30% y 40%) en comparación con el modelo teórico gaussiano. 
</p>

#### 3.3	Ensamblaje Shovell.
<p align="justify">
Tras el depurado de las lecturas crudas, los archivos emparejados procedentes del filtrado con Trimmomatic fueron sometidos a un ensamblaje de novo utilizando el pipeline bioinformático Shovill (v.1.1.0). Este flujo de trabajo automatizado está optimizado para aislamientos bacterianos y coordinó el proceso de estructuración del genoma mediante el motor principal SPAdes.
</p>

##### 3.3.1 Parámetros de entrada y profundidad de secuenciación.
<p align="justify">
El sistema procesó un total de 2,174,830 lecturas individuales (lo que equivale exactamente a los 1,087,415 pares generados en el recorte previo). A partir de la densidad de nucleótidos viables (138.8 Mbp), el algoritmo estimó un tamaño del genoma de 5,000,000 pb (5.0 Mbp), una dimensión estructuralmente consistente con genomas bacterianos como el de Escherichia coli.
Bajo estas métricas, se calculó una profundidad de secuenciación (cobertura) de 27.75X. Al encontrarse por debajo del límite de saturación predeterminado por el software (100X), el algoritmo retuvo y utilizó el 100% de las lecturas de alta calidad provistas, omitiendo procesos de submuestreo para maximizar la resolución del ensamblaje. 
</p>

##### 3.3.2 Motor de ensamblaje (SPAdes) y optimización de K-mers.
<p align="justify">
La construcción del grafo de De Bruijn fue ejecutada por el núcleo de SPAdes. Para optimizar la resolución de regiones repetitivas y asegurar solapamientos precisos, el ensamblador evaluó iterativamente la topología de la secuencia utilizando un rango amplio y escalonado de tamaños de k-mers: 31, 55, 79, 103 y 127. 
</p>

##### 3.3.3 Pulido de consenso y métricas finales.
<p align="justify">
Para garantizar la máxima fidelidad nucleotídica en el producto final, los contigs primarios generados por SPAdes fueron sometidos a una fase de pulido. El pipeline mapeó nuevamente las lecturas limpias contra los contigs crudos utilizando BWA-MEM, y posteriormente ejecutó Pilon para corregir micro-errores de consenso, tales como inserciones, deleciones aisladas y polimorfismos de un solo nucleótido (SNPs) generados durante la síntesis del ensamblador.
El ensamblaje crudo produjo un total de 88 contigs primarios con una longitud total de 4,586,183 pb.
</p>

#### 3.4	Calidad del Ensamblaje (Quast).
<p align="justify">
Para evaluar cuantitativamente la contigüidad, completitud y calidad estructural del borrador genómico generado por Shovill, se empleó la herramienta QUAST (Quality Assessment Tool for Genome Assemblies). Los resultados indican que el ensamblaje es altamente contiguo y representativo del genoma esperado para Escherichia coli, careciendo de brechas (gaps) o bases indeterminadas.
</p>

##### 3.4.1 Métricas Globales del Genoma.
<p align="justify">
El ensamblaje consolidó un total de 69 contigs, sumando una longitud genómica total de 4,586,183 pb (~4.58 Mbp). Esta extensión concuerda perfectamente con el tamaño del genoma de referencia biológico esperado para E. coli (típicamente entre 4.5 y 5.5 Mbp).
El contenido de GC se fijó en 50.60%, un valor característico de esta especie, lo que corrobora que el ensamblaje no sufrió contaminación cruzada con genomas de perfiles nucleotídicos divergentes. Además, la métrica de bases indeterminadas (N's por cada 100 kbp) es de 0.00, demostrando que el algoritmo SPAdes resolvió satisfactoriamente las secuencias sin dejar vacíos o "gaps" internos en los contigs reportados.
</p>

##### 3.4.2 Análisis de Contigüidad (Estadísticos N50 y L50).
<p align="justify">
La robustez de un ensamblaje de novo basado en lecturas cortas (Illumina) se evalúa principalmente a través de la fragmentación del genoma. Los indicadores obtenidos reflejan un alto nivel de integridad estructural:
-	Contig de mayor tamaño (Largest contig): El fragmento continuo más grande alcanzó los 421,689 pb, lo que significa que casi el 10% de todo el genoma bacteriano fue ensamblado en una única secuencia ininterrumpida.
-	N50 y N75: El valor N50 es de 143,876 pb, lo que indica que el 50% de la extensión total del genoma está contenido en contigs de este tamaño o mayores. Asimismo, el N75 de 84,213 pb demuestra que incluso el 75% del genoma está empaquetado en fragmentos de gran tamaño.
-	L50 y L75: El parámetro L50 es 11, revelando que se necesitan únicamente los 11 contigs más grandes para reconstruir la mitad del genoma. Para alcanzar el 75% del genoma (L75), solo se requieren 21 contigs.
</p>

##### 3.4.3 Distribución de la Longitud Acumulada.
<p align="justify">
El gráfico de longitud acumulada (Cumulative length) respalda visualmente la alta calidad del ensamblaje. La curva exhibe un ascenso marcadamente pronunciado en el eje Y (longitud) durante los primeros 20 a 30 contigs en el eje X, para luego aplanarse asintóticamente al acercarse a los 4.58 Mbp.
</p>

#### 3.5	Anotacion Prokka.
<p align="justify">
Una vez validada la integridad y contigüidad del ensamblaje genómico mediante QUAST, los 69 contigs resultantes (abarcando 4,586,183 pb) fueron sometidos a un proceso de anotación automatizada utilizando el pipeline Prokka. 
</p>

##### 3.5.1 Estadísticas Globales de la Anotación.
<p align="justify">
El reporte general generado por el software demuestra un perfil de anotación altamente coherente con la densidad génica esperada para el genoma de Escherichia coli. Se identificaron un total de 4,429 secuencias génicas, distribuidas de la siguiente manera:
</p>
<p align="justify">
-	Secuencias Codificantes (CDS / mRNA): Se predijeron 4,337 secuencias codificantes de proteínas, lo que constituye la inmensa mayoría del catálogo genético y representa el repertorio metabólico y estructural del microorganismo.
-	ARN de Transferencia (tRNA): Se localizaron 88 genes codificantes para tRNAs, una cantidad robusta que garantiza la capacidad del genoma para decodificar los 61 codones de aminoácidos durante la traducción.
-	ARN Ribosomal (rRNA): Se identificaron 3 loci correspondientes a rRNAs, indicando que el ensamblaje logró capturar operones ribosomales, a pesar de que estas regiones repetitivas suelen ser complejas de resolver con tecnologías de lectura corta.
-	ARN mensajero-transferencia (tmRNA): Se detectó 1 locus de tmRNA, esencial para rescatar ribosomas atascados durante la traducción.
</p>

##### 3.5.2 Identificación de Elementos Funcionales Claves (Housekeeping Genes).
<p align="justify">
La evaluación cualitativa de las tablas de características (features) confirma que el proceso de ensamblaje y anotación conservó la estructura de operones vitales y genes de mantenimiento celular (housekeeping), sin evidencias de truncamientos críticos tempranos. 
</p>

### 4. Discusión
interpretación biológica (citar) 

Los resultados obtenidos con QUAST permiten evaluar de forma más clara la calidad del ensamblaje genómico de Escherichia coli.En la figura 35 se presentan indicadores como el número de conting,la longitud total del ensamblaje,el N50,el L50 y el contenido de GC.Estas métricas son importantes porque ayudan a determinar si el genoma emsamblado es continuo,completo y confiable.QUAST y WebQUAST son herramientas usadas para evaluar ensamblajes genómicos mediante este tipo de parámetros (Mikheenko et al., 2023). En este caso el número de contigs indica que el genoma no quedó ensamblado como una sola secuencia completa,sino divido en varios fragmentos.Esto no significa necesariamente que el resultados sea incorrecto,ya que ensamblajes bacterianos obtenidos a partir de lecturas cortas es común encontrar un grado de fragmentación.Sin embargo,mientras menor sea el número de contigs y mayor sea el tamaño de los fragmentos, mejor será la continuidad del ensamblaje. El valor de N50 es un indicador importante,porque permite conocer la longitud de los principales contings del ensamblaje.Un N50 más alto indica que una parte considerable del genoma está representada por fragmentos grandes,lo cual es favorable para continuar con análisis de contigs y la longitud total se consideran métricas centrales para evaluar la calidad y continuidad del ensamblaje (Rojas-miranda et al., 2025).Respecto al contenido de GC,este parámetro ayudar a revisar si el ensamblaje mantiene coherencia biológica con el organismo estudiado.Un contenido GC cercano al esperado para E.coli sugiere que el ensamblaje es consistente y que no existen señales fuertes de errores en las secuencias ensambladas (Quality Check of a Genome Assembly Before Annotation, 2026) .
La figura 36


La anotación funcional obtenida mediante Prokka permitió identificar múltiles elementos genéticos relevantes en el ensamblaje de *Echerichia coli*, incluyendo aproximadamente 4.462 genes, 4.368 CDS, 83 tRNA, 10 rRNA y 1 tmRNA (Figura 14). Estos resultados son consistentes con genomas bacterianos previamente descritos para *E. coli*, los cuales suelen contener entre 4.000 y 5.000 genes codificantes distribuidos en genomas cercanos a 5 Mb (Batut et al., 2024). La presencia de genes codificantes, ARN ribosomal y ARN de transferencia demuestra que el ensamblaje obtenido conserva regiones funcionales esenciales relacionadas con metabolismo, síntesis proteica y regulación celular. Herramientas modernas de anotación como Prokka continúa siendo ampliamente utilizadas debido a su capacidad para integrar bases de datos bacterianas y generar anotaciones rápidas y reproducibles en genomas procariotas (Schwengers et al., 2021). Además, plataformas educativas como Galaxy Training Network proporcionan flujos de trabajo reproducibles para análisis de anotación genómica bacteriana (Galaxy Training Network, 2024).

La tabla de anotación mostrada en la Figura 15 evidencia la identificación de genes asociados con proteínas de membrana, trasnporte de aminoácidos y funciones metabólicas específicas, como metN, metQ, nlpE, nlpE y arfB. Estas funciones son biológicamente relevantes debido a que participan en transporte molecular, respuestas celular y mantenimiento fisiolófico bacteriano. La detección de proteínas hipotéticcas también es común en ensamblajes bacterianos y refleja regiones cuya función aún no ha sido completamente caracterizada experimentalmente (Lobb et al., 2020). En conjunto, los resultados indican que el ensamblaje generado posee suficiente calidad estructural y funcional para estudios posteriores de genómica comparativa, análisis funcional y caracterización de *E. coli*.


### 5. Aplicaciones 

### 5.1 Vigilancia epidemiológica y salud pública

Los resultados obtenidos mediante el ensamblaje con Shovill, la evaluación con QUAST y la anotación funcional con Prokka permiten aplicar herramientas de genómica bacteriana en vigilancia epidemiológica en *Escherichia coli*. La identificación de genes codificantes, regiones funcionales y métricas de calidad del ensamblaje facilita la comparación entre cepas bacterianas y la detección de posibles factores asociados con virulencia o resistencia antimicrobiana. Este tipo de análisis ha sido ampliamente utiliado en el monitoreo de cepas patógenas de *E. coli* involucradas en brotes alimentarios y contaminación ambiental, permitiendo establecer relaciones filogenéticas, identificar genes de resistencia antimicrobiana y rastrear fuentes de infección mediante secuenciación genómica completa (Feldgarden et al., 2021; Schwengers et al., 2021).


### 5.2 Biotecnología y producción de proteínas recombinantes

La información obtenida en este proyecto también tiene aplicación en biotecnología e ingeniería genética, debido a que *Escherichia coli* continúa siendo uno de los principales microorganismos utilizados para producción de proteínas recombinantes y estudios metabólicos. La anotación funcional obtenida mediante Prokka permitió identificar genes asociados con transporte molecular, metabolismo y síntesis proteica, lo cual constituye una base importante para futuras aplicaciones en biología sintética y optimización bacteriana. Actualmente, el análisis genómico y funcional de cepas de *E. coli* es utilizado en el desarrollo de microorganismos destinados a la producción de insulina recombinante, enzimas industriales y compuestos de interés biomédico (Batut et al., 2024; Lobb et al., 2020).


### 6. Conclusiones 


La anotación realizada con Prokka permitió identificar correctamente genes codificantes y elementos funcionales esenciales del genoma de *E. coli*, demostrando que el ensamblaje obtenido es biológicamente interpretabla y adecuado para futuros análisis genómicos y funcionales.

### 7. Referencias bibliográficas  


Batut, B., Hiltemann, S., Bagnacani, A., et al. (2024). The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2024 update. Nucleic Acids Research, 52(W1), W83–W94. https://doi.org/10.1093/nar/gkae410

Feldgarden, M., Brover, V., Gonzalez-Escalona, N., Frye, J. G., Haendiges, J., Haft, D. H., Hoffmann, M., Pettengill, J. B., Prasad, A. B., Tillman, G. E., Tyson, G. H., Klimke, W., & Waterman, M. S. (2021). AMRFinderPlus and the Reference Gene Catalog facilitate examination of the genomic links among antimicrobial resistance, stress response, and virulence. Scientific Reports, 11, 12728. https://doi.org/10.1038/s41598-021-91456-0

Galaxy Training Network. (2024). Assembly of metagenomic sequencing data. Galaxy Project. https://training.galaxyproject.org/training-material/topics/assembly/tutorials/metagenomics-assembly/tutorial.html

Galaxy Training Network. (2024). Genome annotation. Galaxy Project. https://training.galaxyproject.org/training-material/topics/genome-annotation/

Lobb, B., Tremblay, B. J. M., Moreno-Hagelsieb, G., & Doxey, A. C. (2020). An assessment of genome annotation coverage across the bacterial tree of life. Microbial Genomics, 6(3), e000341. https://doi.org/10.1099/mgen.0.000341

Schwengers, O., Jelonek, L., Dieckmann, M. A., Beyvers, S., Blom, J., & Goesmann, A. (2021). Bakta: Rapid and standardized annotation of bacterial genomes via alignment-free sequence identification. Microbial Genomics, 7(11), 000685. https://doi.org/10.1099/mgen.0.000685

Yibar, A., et al. (2024). First report and genomic characterization of Escherichia coli O111 from cattle. BMC Genomics, 25, 10945. https://doi.org/10.1186/s12864-024-10945-4



## NOTA
:eyes: Deberá invitarme a su grupo en Mendeley o las plataformas usadas al correo bioupsmantigua@gmail.comhola
