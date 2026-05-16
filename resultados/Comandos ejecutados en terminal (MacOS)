## Comandos ejecutados en terminal (MacOS)

### Activación del entorno bioinformático

```bash
conda activate bioinfo
```

### Verificación de archivos FASTQ

```bash
ls ~/Downloads | grep SRR38439492
```

### Renombrar archivo descargado

```bash
mv ~/Downloads/"SRR38439492.fastq (1).gz" ~/Downloads/SRR38439492_2.fastq.gz
```

### Ingresar al directorio de trabajo

```bash
cd ~/Downloads
```

### Verificar instalación de FastQC

```bash
which fastqc
```

### Ejecutar FastQC sobre el archivo original

```bash
fastqc SRR38439492.fastq.gz
```

### Abrir reporte HTML generado

```bash
open SRR38439492_fastqc.html
```

---

## Trimming de lecturas con Trimmomatic

### Ejecutar Trimmomatic (single-end)

```bash
trimmomatic SE -phred33 \
SRR38439492.fastq \
SRR38439492_trimmed.fastq \
HEADCROP:10 \
SLIDINGWINDOW:4:20 \
MINLEN:50
```

### Ejecutar FastQC posterior al trimming

```bash
fastqc SRR38439492_trimmed.fastq
```

### Abrir reporte FastQC posterior al trimming

```bash
open SRR38439492_trimmed_fastqc.html
```

---

## Parámetros utilizados

| Parámetro | Función |
|---|---|
| `HEADCROP:10` | Elimina las primeras 10 bases de cada lectura |
| `SLIDINGWINDOW:4:20` | Recorta regiones con calidad promedio menor a Q20 |
| `MINLEN:50` | Descarta lecturas menores a 50 pb |
| `-phred33` | Define codificación de calidad Illumina moderna |

```
