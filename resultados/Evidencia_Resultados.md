# CAPTURAS DE PANTALLA DE RESULTADOS OBTENIDOS

## 1. Descarga de secuencia

### 1.1 Forward

<img width="324" height="228" alt="image" src="https://github.com/user-attachments/assets/7c2d89e0-34a6-4009-a477-63f64f27ad5f" />

Figura 8. Información del Dataset a partir de la herramienta Download and Extract Reads in FASTQ de la secuencia Forward. 


### 1.2 Reverse

<img width="339" height="228" alt="image" src="https://github.com/user-attachments/assets/2b03998e-e279-4aea-8600-18470fb4660d" />

Figura 9. Información del Dataset a partir de la herramienta Download and Extract Reads in FASTQ de la secuencia Reverse 


## 2. Analizar la calidad de la secuencia obtenida -FastQ- 

### 2.1	Reporte FastQC para calidad de secuencias. Forward 

<img width="345" height="228" alt="image" src="https://github.com/user-attachments/assets/cc0eb8fc-2d7b-45e7-aedb-0fa7bb4715c4" />

Figura 10. Resumen del reporte FastQC secuencia Forward 


<img width="335" height="257" alt="image" src="https://github.com/user-attachments/assets/fb66df37-1073-42dc-95d0-de89a7d31367" />

Figura 11.  Gráfico de la calidad de Secuencias por Base, secuencia Forward. 


<img width="368" height="277" alt="image" src="https://github.com/user-attachments/assets/5a4c9daa-ef0d-4b0f-aeff-d80ce48cf0d2" />

Figura 12.  Gráfico de la calidad de Secuencias por celda, secuencia Forward.


<img width="363" height="272" alt="image" src="https://github.com/user-attachments/assets/e83ec109-9822-46b2-adbb-d80ed2fbe064" />

Figura 13.  Gráfico del contenido de Secuencias por base, secuencia Forward. 


<img width="370" height="271" alt="image" src="https://github.com/user-attachments/assets/4d463a17-fb90-4389-8715-29f8b6758657" />

Figura 14.  Gráfico del contenido de GC por secuencia, secuencia Forward. 


### 2.2	2.	Reporte FastQC para calidad de secuencias. Reverse

<img width="328" height="221" alt="image" src="https://github.com/user-attachments/assets/cdb1595f-ec34-4596-8ae3-34c399256b1b" />

Figura 15.  Resumen del reporte FastQC secuencia Reverse. 


<img width="346" height="257" alt="image" src="https://github.com/user-attachments/assets/06dcac4e-aa9e-4804-ac50-fd6592dde6aa" />

Figura 16.  Gráfico de la calidad de Secuencias por Base, secuencia Reverse. 


<img width="334" height="259" alt="image" src="https://github.com/user-attachments/assets/ed9b6943-5341-4f9b-b46c-8e5df6f81b17" />

Figura 17.  Gráfico de la calidad de Secuencias por celda, secuencia Reverse. 


<img width="335" height="251" alt="image" src="https://github.com/user-attachments/assets/a788189a-2d1d-4f0d-9614-021603ee7fba" />

Figura 18.  Gráfico del contenido de Secuencias por base, secuencia Reverse. 


<img width="353" height="263" alt="image" src="https://github.com/user-attachments/assets/30ff5344-2a82-42d0-84b4-658273faffc2" />

Figura 19.  Gráfico del contenido de GC por secuencia, secuencia Reverse. 


## 3. Primer corte y limpieza de la secuencia (Trimmomatic)

<img width="442" height="253" alt="image" src="https://github.com/user-attachments/assets/3c817f2c-7415-41f2-85cb-8b6c23dfca84" />

Figura 20. Visualización del primer corte de la secuencia Forward 

 

 
 <img width="600" height="270" alt="imagen 1" src="https://github.com/user-attachments/assets/fbb7c643-87df-40ea-b7cd-7881af66e6ad" />
Figura 26. Reporte de calidad generado por FastQC para la lectura Reverse después del filtrado con Trimmomatic. 

<img width="600" height="345" alt="imagen 2" src="https://github.com/user-attachments/assets/38dc3cba-53f9-40f8-ba98-1ec41d7be1ae" />

Figura 27. Grafica de la calidad por base de la secuencia Reverse filtrada donde reserve conserva una calidad alta después del recorte. 
<img width="600" height="354" alt="28" src="https://github.com/user-attachments/assets/2e33e75e-c625-4a53-bbe8-6c1eaf86d80d" />

Figura 28. Calidad por tilde de la secuencia Reverse filtrada  

<img width="600" height="345" alt="29" src="https://github.com/user-attachments/assets/059f370b-cdb0-485b-855d-0391f5bf883a" />

Figura 29. Grafica de la distribución estable de nucleótidos de la lectura Reverse. Esto indica que, después de la limpieza los datos son adecuados para el ensamblaje 

<img width="600" height="437" alt="30" src="https://github.com/user-attachments/assets/35037154-fe2e-459f-9ee2-7ba3b26457c9" />


Figura 30. Curva del contenido final de GC de la secuencia Reverse filtrada 

<img width="600" height="287" alt="31" src="https://github.com/user-attachments/assets/1010f2c3-eb5d-4f37-908a-700e878b0b3c" />


Figura 31. Ensamblaje de novo mediante Shovill en Galaxy lo cual permitió unir lecturas Forward y Reverse. 

<img width="600" height="343" alt="32" src="https://github.com/user-attachments/assets/68b5f55a-ff16-4206-b51c-6580772d4139" />


Figura 32. Archivos de contings generado por Shovill en formato FASTA que serán usados para evaluar la calidad del ensamblaje 

<img width="600" height="464" alt="33" src="https://github.com/user-attachments/assets/a6c4edb1-6e26-428c-bc7c-1e038ca019bd" />

Figura 33. Evaluación del ensamblaje con QUAST con indicadores del ensamblaje como números de contings, longitud total., n50, L50 y contenido de GC. 
<img width="600" height="319" alt="34" src="https://github.com/user-attachments/assets/c6b562f1-5f0e-4370-b22c-8d2c2e9f0613" />


Figura 34. Curva acumulada de longitud de contings 
<img width="604" height="275" alt="35" src="https://github.com/user-attachments/assets/86038a2c-9e3f-4cc7-a155-79085a6c135b" />

Figura 35. Resumen generado por Prokka,donde se identifican genes,CDS,rRNA,tRNA y tmRNA. 
<img width="600" height="426" alt="36" src="https://github.com/user-attachments/assets/0c9b5e87-fc8d-402e-b0b6-e8197c449791" />


Figura 36. Tabla de genes anotados en Prokka con información relacionada con la ubicación, tipo de elemento genético y función. 

 <img width="553" height="403" alt="3737" src="https://github.com/user-attachments/assets/93dd947a-7465-4983-8f6b-5878c76d6c44" />

Figura 37. Tabla generada por Prokka de genes codificantes y posibles productos proteicos 
<img width="551" height="397" alt="3838" src="https://github.com/user-attachments/assets/c78e6da5-0a76-48c7-8d0c-884940eca18f" />


Figura 38. Anotación funcional de regiones genómicas 
 
<img width="551" height="343" alt="3939" src="https://github.com/user-attachments/assets/b54ddafc-d0be-4f4d-adb1-7c082a9e1d45" />

Figura 39. Resultados finales de la anotación genómica realizados en Prokka. 
