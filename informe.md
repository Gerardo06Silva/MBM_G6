# Proyecto: Análisis de calidad, ensamblaje y caracterización genómica de Escherichia coli a partir de secuencias FASTQ  

## Integrantes
- Gerardo Silva
- Katherine Cevallos
- Johanna Montenegro P.

## Objetivo
Procesar lecturas FASTQ de Escherichia coli mediante control de calidad, depuración y ensamblaje de novo, con el fin de obtener una secuencia genómica evaluable e identificar parámetros relevantes como longitud del ensamblaje, contenido GC, cobertura y posibles regiones codificantes.

### 1. Introducción
Echerichia coli es uno de los microorganismos modelo más utilizados en biología molecular, microbiología y bioinformática debido a que posee un genoma relativamente pequeño, ampliamente caracterizado y disponible en múltiples bases de datos genómicas públicas. Además de su importancia como organismo modelo, algunas cepas de E. coli tienen relevancia clínica y biotecnológica, ya que pueden participar en procesos industriales, producción de proteínas recombinantes y estudios relacionados con resistencia antimicrobiana y evolución bacteriana (Yibar et al., 2024).

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



La anotación funcional obtenida mediante Prokka permitió identificar múltiles elementos genéticos relevantes en el ensamblaje de *Echerichia coli*, incluyendo aproximadamente 4.462 genes, 4.368 CDS, 83 tRNA, 16 rRNA y 1 tmRNA (Figura ***). Estos resultados son consistentes con genomas bacterianos previamente descritos para *E. coli*, los cuales suelen contener entre 4.000 y 5.000 genes codificantes distribuidos en genomas cercanos a 5 Mb (Batut et al., 2024). La presencia de genes codificantes, ARN ribosomal y ARN de transferencia demuestra que el ensamblaje obtenido conserva regiones funcionales esenciales relacionadas con metabolismo, síntesis proteica y regulación celular. Herramientas modernas de anotación como Prokka continúa siendo ampliamente utilizadas debido a su capacidad para integrar bases de datos bacterianas y generar anotaciones rápidas y reproducibles en genomas procariotas (Schwengers et al., 2021).

La tabla de anotación mostrada en la figura *** evidencia la identificación de genes asociados con proteínas de membrana, trasnporte de aminoácidos y funciones metabólicas específicas, como metN, metQ, nlpE, nlpE y arfB. Estas funciones son biológicamente relevantes debido a que participan en transporte molecular, respuestas celular y mantenimiento fisiolófico bacteriano. La detección de proteínas hipotéticcas también es común en ensamblajes bacterianos y refleja regiones cuya función aún no ha sido completamente caracterizada experimentalmente (Lobb et al., 2020). En conjunto, los resultados indican que el ensamblaje generado posee suficiente calidad estructural y funcional para estudios posteriores de genómica comparativa, análisis funcional y caracterización de *E. coli*.

### 5. Conclusiones 


La anotación realizada con Prokka permitió identificar correctamente genes codificantes y elementos funcionales esenciales del genoma de *E. coli*, demostrando que el ensamblaje obtenido es biológicamente interpretabla y adecuado para futuros análisis genómicos y funcionales.
La evaluación realizada con QUAST ayudó a comprobar que, aunque el genoma no quedó unido en una sola secuencia completa, los resultados obtenidos muestran una buena calidad del ensamblaje. Los valores de N50, L50 y la curva acumulada de contigs indican que gran parte del genoma fue reconstruida en fragmentos amplios y ordenados. En este sentido, el flujo de trabajo bioinformático aplicado fue adecuado, ya que permitió procesar las lecturas FASTQ, limpiar los datos, ensamblarlos y obtener información genómica importante de *Escherichia coli*.

### 6. Referencias bibliográficas  
Genere un grupo en Mendeley con sus compañeros de proyecto. Coloque todas sus fuentes y los respectivos PDFs de cada una 


Batut, B., et al. (2024). Assembly of metagenomic sequencing data. Galaxy Training Network. https://training.galaxyproject.org/training-material/topics/assembly/tutorials/metagenomics-assembly/tutorial.html

Batut, B., Hiltemann, S., Bagnacani, A., et al. (2024). The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2024 update. Nucleic Acids Research, 52(W1), W83–W94. https://doi.org/10.1093/nar/gkae410

Lobb, B., Tremblay, B. J. M., Moreno-Hagelsieb, G., & Doxey, A. C. (2020). An assessment of genome annotation coverage across the bacterial tree of life. Microbial Genomics, 6(3), e000341. https://doi.org/10.1099/mgen.0.000341

Schwengers, O., Jelonek, L., Dieckmann, M. A., Beyvers, S., Blom, J., & Goesmann, A. (2021). Bakta: Rapid and standardized annotation of bacterial genomes via alignment-free sequence identification. Microbial Genomics, 7(11), 000685. https://doi.org/10.1099/mgen.0.000685

Yibar, A., et al. (2024). First report and genomic characterization of Escherichia coli O111 from cattle. BMC Genomics, 25, 10945. https://doi.org/10.1186/s12864-024-10945-4



## NOTA
:eyes: Deberá invitarme a su grupo en Mendeley o las plataformas usadas al correo bioupsmantigua@gmail.comhola
