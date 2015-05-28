---
title: "README.md"
author: "Javier F. Tabima e Ivania Ceron-Souza"
date: "May 28, 2015"
output: html_document
---

Para determinar el numero de reads nefcesarios para estudiar el transcriptoma, vamos a obtener la base de datos de todas las secuencias trascritas de *Rhizophora mangle* de [La Universidad de Illinois](http://mangrove.illinois.edu/).

# Numero de pares de bases necesarias para secuenciar el transcriptoma al menos una vez

La idea es calcular el numero de pares de bases necesarias para obtener al menos 1x del genoma:

```
1x del genoma = Sumatoria(Longitud de cada transcrito)
```

Por ahora, vamos a hacer los calculos con los datos generales (Tabla 1, [Dassanayake et al, 2009](http://onlinelibrary.wiley.com/doi/10.1111/j.1469-8137.2009.02913.x/abstract):

 * Numero de contigs: 25,535
 
 * Promedio de tamaño de cada contig: 433 bp
 
 ```
 1x del genoma = 25,535 * 433 = 11,056,655 de pares de bases 
 ```
 
Vamos a necesitar un total de 11,056,655 de pares de bases para secuenciar el transcriptoma al menos una vez.

# Numero de pares de bases obtenidas por HiSeq-3000

Illumina y [Otra gente](https://biomickwatson.wordpress.com/2015/01/12/putting-the-hiseq-4000-in-context/) dicen que hay un promedo de reads por lane de 378'000,000 reads. Segun esto, el numero de pares de bases que vamos a obtener es de:

```
378'000,000 reads por lane * 150bp = 56,700,000,000 pares de bases
```

# Cobertura por lane para una muestra de *Rhizophora*

Si para 1x de *R. mangle* tenemos 11,056,655 bp, cuanto es la cobertura promedio en un lane del 3000?

```
56,700,000,000 bp/ 11,056,655bp = 5,128.133x
```

Tenemos una cobertura absurda de mas de 5,000x por muestra. Ahora, supongamos que solo queremos una covertura promedio de 7x (comparandolo con el paper de [Dassanayake et al, 2009](http://onlinelibrary.wiley.com/doi/10.1111/j.1469-8137.2009.02913.x/abstract)):

```
7x = 11,056,655bp * 7 = 77,396,585pb para 7x
```

Entonces, el numero de muestras que pueden haber para 7x de cobertura promedio es:

```
56,700,000,000 bp/ 77,396,585 = 732 muestras per lane
```

El numero es demasiado alto, pero podria ser real. 

> Nota 1: Recordar que son promedios y escribirle a los autores para pedirles el transcriptoma (Por que sonbre este vamos a mapear los reads)
> Nota 2: Preguntar al CGRB sobre numeros de reads de RNAseq para paired end reads de 150bp para el HiSeq-3000


Entonces, si tenemos 21 muestras de acuerdo a el esquema de Ivi, para 7x de cobertura:

```
56,700,000,000 bp/ (21 samples * 77,396,585 bp) = 34x por muestra
```

> Nota 3: Puede que hayan transcritos ALTAMENTE representados, y cambien los datos. Cuidado con esto.
