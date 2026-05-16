# Proyecto: Análisis de calidad, ensamblaje y caracterización genómica de Escherichia coli a partir de secuencias FASTQ  

## Integrantes
- Gerardo Silva
- Katherine Cevallos
- Johanna Montenegro P.

## Objetivo
Procesar lecturas FASTQ de Escherichia coli mediante control de calidad, depuración y ensamblaje de novo, con el fin de obtener una secuencia genómica evaluable e identificar parámetros relevantes como longitud del ensamblaje, contenido GC, cobertura y posibles regiones codificantes.

### 1. Introducción
Escherichia coli es uno de los microorganismos modelo más utilizados en biología molecular, microbiología y bioinformática debido a que posee un genoma relativamente pequeño, ampliamente caracterizado y disponible en múltiples bases de datos genómicas públicas. Además de su importancia como organismo modelo, algunas cepas de E. coli tienen relevancia clínica y biotecnológica, ya que pueden participar en procesos industriales, producción de proteínas recombinantes y estudios relacionados con resistencia antimicrobiana y evolución bacteriana (Yibar et al., 2024).

El desarrollo de tecnologías de secuenciación masiva ha permitido generar grandes volúmenes de datos genómicos bacterianos en formatos como FASTQ, facilitantdo el análisis bioinformático de genomas completos mediante flujos de trabajo de ensamblaje y anotación. Actualmente, herramientas como FastQC, Trimmomatic, SPAdes, QUAST y Prokka son ampliamente utilizadas para evaluar calidad de lecturas, ensamblar genomas de novo y caracterizar regiones funcionales bacterianas (Batut et al., 2024). Estas herramientas permiten obtener métricas importantes como contenido GC, número de contigs, continuidad del ensamblaje y predicción de genes codificantes.

En este proyecto se trabajó con secuencias WGS (Whole Genome Sequencing) de Echerichia coli obtenidas desde el repositorio SRA del NCBI, específicamente el dataset SRR38439492. El objetivo fue procesar lecturas FASTQ mediante control de calidad, depuración y ensamblaje de novo, con el fin de obtener un ensamblaje genómico evaluable e identificar parámetros relevantes como longitud del ensamblaje, cobertura y regiones potencialmente codificantes. Este tipo de análisis constituye una base fundamental para estudios de genómica comparativa, evolución bacteriana y caracterización funcional de microorganismos procariotas (Schwengers et al., 2021).


### 2. Metodología  
En primer lugar, se obtuvieron las secuencias crudas en formato FASTQ desde la base de datos NCBI SRA. Estos archivos contienen las lecturas generadas por secuenciación, junto con la información de calidad de cada base. La descarga de los datos se realizó mediante herramientas como NCBI SRA y la plataforma Galaxy, obteniendo como resultado los archivos FASTQ iniciales.  
Posteriormente, se realizó un control de calidad inicial utilizando FastQC. Se revisaron aspectos como la calidad de las bases, la presencia de adaptadores, el contenido GC, la longitud de las secuencias y posibles duplicaciones. Con esta información se pudo decidir si las lecturas eran adecuadas o si necesitaban una limpieza previa.  
Cuando las lecturas no cumplían completamente con los criterios de calidad, se aplicó un proceso de limpieza y filtrado usando herramientas como Trimmomatic y fastp. Este paso permitió eliminar fragmentos de baja calidad, adaptadores y secuencias muy cortas que podrían afectar los resultados posteriores. Como resultado, se obtuvieron lecturas más limpias y confiables para el ensamblaje del genoma.  
Una vez obtenidas las lecturas limpias, se procedió al ensamblaje del genoma mediante la herramienta Shovill. Esta etapa consistió en unir las lecturas que compartían regiones similares para formar secuencias más largas llamadas contigs. Estos contigs representan fragmentos reconstruidos del genoma de E. coli y constituyen la base para los análisis siguientes.  
Después del ensamblaje, se evaluó su calidad utilizando QUAST. En esta fase se analizaron métricas como el valor N50, la longitud total del ensamblaje, el número de contigs y el porcentaje de GC. Estos indicadores permitieron determinar si el ensamblaje era adecuado y si los resultados obtenidos eran coherentes con lo esperado para un genoma bacteriano.  
Si el ensamblaje no cumplía con los criterios esperados, se regresaba a revisar la calidad de las lecturas, los parámetros de limpieza y las condiciones del ensamblaje.  Cuando el ensamblaje fue considerado aceptable, se realizó la anotación del genoma utilizando Prokka. Esta herramienta permitió identificar los principales elementos genéticos presentes en el genoma ensamblado, como regiones codificantes, genes, CDS, RNA y tRNA.  
Finalmente, se obtuvo un genoma de E. coli ensamblado, evaluado y anotado.  
<img width="297" height="419" alt="image" src="https://github.com/user-attachments/assets/67ca0129-4e5b-4a8c-b789-fdaa4345e742" />
  
### 3. Resultados
tablas 
gráficos
interpretación biológica 

### 4. Discusión
interpretación biológica (citar) 

Los resultados obtenidos con QUAST permiten evaluar de forma más clara la calidad del ensamblaje genómico de Escherichia coli.En la figura 35 se presentan indicadores como el número de conting,la longitud total del ensamblaje,el N50,el L50 y el contenido de GC.Estas métricas son importantes porque ayudan a determinar si el genoma emsamblado es continuo,completo y confiable.QUAST y WebQUAST son herramientas usadas para evaluar ensamblajes genómicos mediante este tipo de parámetros (Mikheenko et al., 2023). En este caso el número de contigs indica que el genoma no quedó ensamblado como una sola secuencia completa,sino divido en varios fragmentos.Esto no significa necesariamente que el resultados sea incorrecto,ya que ensamblajes bacterianos obtenidos a partir de lecturas cortas es común encontrar un grado de fragmentación.Sin embargo,mientras menor sea el número de contigs y mayor sea el tamaño de los fragmentos, mejor será la continuidad del ensamblaje. El valor de N50 es un indicador importante,porque permite conocer la longitud de los principales contings del ensamblaje.Un N50 más alto indica que una parte considerable del genoma está representada por fragmentos grandes,lo cual es favorable para continuar con análisis de contigs y la longitud total se consideran métricas centrales para evaluar la calidad y continuidad del ensamblaje (Rojas-miranda et al., 2025).Respecto al contenido de GC,este parámetro ayudar a revisar si el ensamblaje mantiene coherencia biológica con el organismo estudiado.Un contenido GC cercano al esperado para E.coli sugiere que el ensamblaje es consistente y que no existen señales fuertes de errores en las secuencias ensambladas (Quality Check of a Genome Assembly Before Annotation, 2026) .
La figura 36


La anotación funcional obtenida mediante Prokka permitió identificar múltiles elementos genéticos relevantes en el ensamblaje de *Echerichia coli*, incluyendo aproximadamente 4.462 genes, 4.368 CDS, 83 tRNA, 10 rRNA y 1 tmRNA (Figura ***). Estos resultados son consistentes con genomas bacterianos previamente descritos para *E. coli*, los cuales suelen contener entre 4.000 y 5.000 genes codificantes distribuidos en genomas cercanos a 5 Mb (Batut et al., 2024). La presencia de genes codificantes, ARN ribosomal y ARN de transferencia demuestra que el ensamblaje obtenido conserva regiones funcionales esenciales relacionadas con metabolismo, síntesis proteica y regulación celular. Herramientas modernas de anotación como Prokka continúa siendo ampliamente utilizadas debido a su capacidad para integrar bases de datos bacterianas y generar anotaciones rápidas y reproducibles en genomas procariotas (Schwengers et al., 2021).

La tabla de anotación mostrada en la figura *** evidencia la identificación de genes asociados con proteínas de membrana, trasnporte de aminoácidos y funciones metabólicas específicas, como metN, metQ, nlpE, nlpE y arfB. Estas funciones son biológicamente relevantes debido a que participan en transporte molecular, respuestas celular y mantenimiento fisiolófico bacteriano. La detección de proteínas hipotéticcas también es común en ensamblajes bacterianos y refleja regiones cuya función aún no ha sido completamente caracterizada experimentalmente (Lobb et al., 2020). En conjunto, los resultados indican que el ensamblaje generado posee suficiente calidad estructural y funcional para estudios posteriores de genómica comparativa, análisis funcional y caracterización de *E. coli*.


### 5. Aplicaciones 

### 5.1 Vigilancia epidemiológica y salud pública

Los resultados obtenidos mediante el ensamblaje con Shovill, la evaluación con QUAST y la anotación funcional con Prokka permiten aplicar herramientas de genómica bacteriana en vigilancia epidemiológica en *Escherichia coli*. La identificación de genes codificantes, regiones funcionales y métricas de calidad del ensamblaje facilita la comparación entre cepas bacterianas y la detección de posibles factores asociados con virulencia o resistencia antimicrobiana. Este tipo de análisis ha sido ampliamente utiliado en el monitoreo de cepas patógenas de *E. coli* involucradas en brotes alimentarios y contaminación ambiental, permitiendo establecer relaciones filogenéticas y rastrear fuentes de infección mediante secuenciación genómica completa (Allard et al., 2021; Schwengers et al., 2021).


### 5.2 Biotecnología y producción de proteínas recombinantes

La información obtenida en este proyecto también tiene aplicación en biotecnología e ingeniería genética, debido a que *Escherichia coli* continúa siendo uno de los principales microorganismos utilizados para producción de proteínas recombinantes y estudios metabólicos. La anotación funcional obtenida mediante Prokka permitió identificar genes asociados con transporte molecular, metabolismo y síntesis proteica, lo cual constituye una base importante para futuras aplicaciones en biología sintética y optimización bacteriana. Actualmente, el análisis genómico y funcional de cepas de *E. coli* es utilizado en el desarrollo de microorganismos destinados a la producción de insulina recombinante, enzimas industriales y compuestos de interés biomédico (Batut et al., 2024; Lobb et al., 2020).


### 6. Conclusiones 


La anotación realizada con Prokka permitió identificar correctamente genes codificantes y elementos funcionales esenciales del genoma de *E. coli*, demostrando que el ensamblaje obtenido es biológicamente interpretabla y adecuado para futuros análisis genómicos y funcionales.

### 7. Referencias bibliográficas  
Genere un grupo en Mendeley con sus compañeros de proyecto. Coloque todas sus fuentes y los respectivos PDFs de cada una 


Allard, M. W., Bell, R., Ferreira, C. M., Gonzalez-Escalona, N., Hoffmann, M., Muruvanda, T., Ottesen, A., Ramachandran, P., Reed, E., Sharma, S., Stevens, E., Timme, R., Wang, C., & Brown, E. W. (2021). Genomics of foodborne pathogens for microbial food safety. Current Opinion in Biotechnology, 70, 91–98. https://doi.org/10.1016/j.copbio.2021.05.002

Batut, B., et al. (2024). Assembly of metagenomic sequencing data. Galaxy Training Network. https://training.galaxyproject.org/training-material/topics/assembly/tutorials/metagenomics-assembly/tutorial.html

Batut, B., et al. (2024). Genome annotation and comparative genomics workflows in Galaxy Training Network. Galaxy Project. https://training.galaxyproject.org/training-material/topics/genome-annotation/

Batut, B., Hiltemann, S., Bagnacani, A., et al. (2024). The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2024 update. Nucleic Acids Research, 52(W1), W83–W94. https://doi.org/10.1093/nar/gkae410

Lobb, B., Tremblay, B. J. M., Moreno-Hagelsieb, G., & Doxey, A. C. (2020). An assessment of genome annotation coverage across the bacterial tree of life. Microbial Genomics, 6(3), e000341. https://doi.org/10.1099/mgen.0.000341

Schwengers, O., Jelonek, L., Dieckmann, M. A., Beyvers, S., Blom, J., & Goesmann, A. (2021). Bakta: Rapid and standardized annotation of bacterial genomes via alignment-free sequence identification. Microbial Genomics, 7(11), 000685. https://doi.org/10.1099/mgen.0.000685

Yibar, A., et al. (2024). First report and genomic characterization of Escherichia coli O111 from cattle. BMC Genomics, 25, 10945. https://doi.org/10.1186/s12864-024-10945-4



## NOTA
:eyes: Deberá invitarme a su grupo en Mendeley o las plataformas usadas al correo bioupsmantigua@gmail.comhola
