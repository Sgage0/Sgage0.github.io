<h4># Subread, avialable at https://subread.sourceforge.net/ , is a powerful suite of analysis functions. Once installed, you establish an environment in miniconda, and run Subread functions in that environment.</h4>
<h4># For instance, after entering my "Lab" environment, I am attempting to quantitate the number of each transcript from a pair-ended sequencing transcriptome for six sample cells, three controls, a.bam, b.bam, and c.bam, as well as three knockdowns, 1.bam, 2.bam, and 3.bam:</h4>

```
$ featureCounts -a referenceGenome.gtf -t exon -g gene_id -p -o counts.txt a.bam b.bam c.bam 1.bam 2.bam 3.bam
```

<h4># The parameters in the above example are -a precedes the annotated reference genome (.gtf format), -t for type of data to be analyzed (default is "exon"), -g groups features into metafeatures (with the default being exons grouped into gene identifiers), -p for pair-ended reads, -o precedes the output_file ("counts.txt" in the example), and arguments following the specified output.</h4>

<h4># In the above example, featureCounts will output a .txt file, with the file name "counts.txt". The number of columns in the file is equal to the number of samples analyzed, one row for each detected group specified by -g, and the value of each cell equal to the number of times the transcript was detected in the experiment. The .txt file can easily be used as a dataframe or opened with a spreadsheet application like LibreOffice Calc after a simple extension chnage to .csv (although I do not recommend reading the .csv file, except for row names, it is difficult to follow).</h4>

<h4># For example, the head (first four lines) of my data output from counts.txt:</h4>


```
# Program:featureCounts v2.0.3; Command:"featureCounts" "-p" "--countReadPairs" "-a" "referenceGenome.gtf" "-t" "exon" "-g" "gene_id" "-o" "counts.txt" "a.bam" "b.bam" "c.bam" "1.bam" "2.bam" "3.bam" 

Geneid	Chr	Start	End	Strand	Length	a.bam	b.bam	c.bam	1.bam	2.bam	3.bam

Foo	chrA;chrA;chrA;chrA;chrA;chrA	n1;n2;n3;n4;n5;n6	n7;n8;n9;n10;n11;n12	+;+;+;+;+;+	nlength1	0	0	0	0	0	0

Bar	chrH;chrH	n13;n14	n15;n15	-;-	nlength2	253	337	268	314	266	196

Baz	chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA;chrA	n16;n17;n18;n19;n20;n21;n22;n23;n24;n25;n26;n27;n28;n29;n30;n31 n32;n33;n34;n35;n36;n37;n38;n39;n40;n41;n42;n43;n44;n45;n46;n47	+;+;+;+;+;+;+;+;+;+;+;+;+;+;+;+	nlength3	361	391	416	371	407	410

```

<h4># In this sample output text, the first line identifies the command, arguments, and parameters used to generate the data. The second line are the column headers, including "Geneid" (Gene-identification), "Chr" (Chromosome), "Start" (base number for starting base pair), "End" (base number for ending base pair), "Strand" (output is either "+" or "-"), "Length" (length of the feature), and then one entry for each NGS data set where transcripts were detected. For the "Chr", "Start", "End", and "Strand" columns, multiple exons are reported, with each value separated by a semicolon; 6/6 exons are tested for Foo, 2/2 exons are tested for Bar, and 16/20 exons are tested for Baz. n#, basepair number; nlength#, length of the feature. Note Foo was not detected, while bar was detected in all six data sets at least 196 times.</h4>

<h4># Helpfully, the .txt output of featureCounts can be accepted as an argument in edgeR to be able to determine knockdown or increases in expression, along with statistical significant and false discovery rate. More on this with a description of edgeR.</h4>

<h4># Subread also comes with an R compatible "Rsubread". Hoewver, I was initially practicing NGS analysis, I was advised Subread run using miniconda is able to manage larger data sets faster than Rsubread.</h4>
