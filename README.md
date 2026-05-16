# MBM_G6
Herramientas Ómicas 1  
Grupo 6
<p align="justify">
  
# Proyecto: Análisis de calidad, ensamblaje y caracterización genómica de <i>Escherichia coli</i> a partir de secuencias FASTQ
</p>

## 1. Integrantes
- Gerardo Silva
- Katherine Cevallos
- Johanna Montenegro P.
  
## 2. Objetivo
<p align="justify">
Procesar lecturas FASTQ de <i>Escherichia coli</i> mediante control de calidad, depuración y ensamblaje de novo, con el fin de obtener una secuencia genómica evaluable e identificar parámetros relevantes como longitud del ensamblaje, contenido GC, cobertura y posibles regiones codificantes.  
</p>
  
## 3. Dataset
Se utilizaron secuencias públicas de <i>Escherichia coli</i> obtenidas desde:  
- NCBI SRA  
SRX33263328: WGS of <i>Escherichia coli</i>  
https://www.ncbi.nlm.nih.gov/sra/?term=SRX33263328  
<img width="489" height="79" alt="image" src="https://github.com/user-attachments/assets/78716019-c444-4367-a96a-d73f56392abf" />

Formato:
- FASTQ (lecturas crudas)
  
## 4. Flujo de trabajo
<p align="justify">
El tutorial que se está utilizando como modelo para el proyecto corresponde al tutorial 2 “Assembly of metagenomic sequencing data”, de la lista de tutoriales proporcionados por la herramienta bioinformatica Galaxy. 
<br>
Link: https://training.galaxyproject.org/training-material/topics/assembly/tutorials/metagenomics-assembly/tutorial.html  
</p>  
<p align="center">
<img width="297" height="419" alt="image" src="https://github.com/user-attachments/assets/0d7064c2-e8c6-4dc5-9e9a-e7bbd639c40e" />
</p>

## 5. Resultados  
<p align="justify">
El ensamblaje de <i>Escherichia coli</i> presentó 109 contigs, una longitud total de 4.707.967 pb y un contenido GC de 50,57 %, valores coherentes con lo esperado para esta especie. El contig más largo fue de 286.319 pb, con un N50 de 113.582 pb y un L50 de 14, lo que indica una continuidad moderada del ensamblaje. Además, la ausencia de bases ambiguas (0 N por 100 kbp) representa un indicador positivo de calidad.
</p>

<p align="justify">
En conjunto, los resultados son aceptables para un ensamblaje preliminar con lecturas Illumina, aunque los 109 contigs evidencian que el genoma aún está fragmentado. La anotación con Prokka identificó aproximadamente 4.462 genes, 4.368 CDS, 83 tRNAs, 16 rRNAs y 1 tmRNA, lo que demuestra que el ensamblaje contiene regiones funcionales suficientes para futuros análisis de anotación, metabolismo bacteriano y comparación genómica.  
</p>

## 6. Contribución individual  
<p align="justify">

- **Gerardo Silva:** selección de secuencias a estudiar, corrida de herramientas dentro de Galaxy, interacción con Github. 
- **Katherine Cevallos:** descripción de datos, workflow del proyecto, interacción con Github. 
- **Johanna Montenegro:** justificación de la selección del microorganismo a estudiar, planteamiento de hipótesis, interpretación biológica de los resultados, interacción con Github.

</p>

## 7. Cómo reproducir (scripts)  

<p align="justify">
Se eligió esta secuencia por sus características.  
Debe ser una secuencia WGS (whole genome secuence) para evitar metagenomas o microbiomas, además de tener un peso de 169.1 MB y 1 106,152 de spots para asegurar una cobertura apropiada para ensamblar el genoma.  
  
Para reproducir este workflow se debe seguir el History ejecutado dentro de la plataforma Galaxy.  
https://usegalaxy.org/u/gerardoalex/h/mbm-g6-workflow-secuencia-e-coli  
</p>  

El Flujo general seguido sera:
```text
Descarga de archivos FASTQ crudo mediante el codigo SRR para  NCBI
 ↓
Control de calidad (FastQC) a las secuencias descargadas
 ↓
Trimming (Trimmomatic) Se realiza cortes y limpieza dentro de la secuencia descargada.
 ↓
Ensamblaje (Shovill)
 ↓
Evaluación del ensamblaje (Quast)
 ↓
Anotación (Prokka)
```
