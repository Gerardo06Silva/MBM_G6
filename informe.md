# Proyecto: Análisis de calidad, ensamblaje y caracterización genómica de Escherichia coli a partir de secuencias FASTQ  

## Integrantes
- Gerardo Silva
- Katherine Cevallos
- Johanna Montenegro P.

## Objetivo
Procesar lecturas FASTQ de Escherichia coli mediante control de calidad, depuración y ensamblaje de novo, con el fin de obtener una secuencia genómica evaluable e identificar parámetros relevantes como longitud del ensamblaje, contenido GC, cobertura y posibles regiones codificantes.

### 1. Introducción
contexto biológico
importancia del análisis

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

### 5. Conclusiones  

### 6. Referencias bibliográficas  
Genere un grupo en Mendeley con sus compañeros de proyecto. Coloque todas sus fuentes y los respectivos PDFs de cada una  
## NOTA
:eyes: Deberá invitarme a su grupo en Mendeley o las plataformas usadas al correo bioupsmantigua@gmail.comhola
