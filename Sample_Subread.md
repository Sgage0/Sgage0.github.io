<h3># Subread, avialable at https://subread.sourceforge.net/ , is a powerful suite of analysis functions. Once installed, you establish an environment in miniconda, and run Subread functions in that environment.</h3>
<h3># For instance, after entering my "Lab" environment, I am attempting to quantitate the number of each transcript from a pair-ended sequencing transcriptome for six sample cells, three controls, a.bam, b.bam, and c.bam, as well as three knockdowns, 1.bam, 2.bam, and 3.bam:</h3>

```
$ featureCounts -a referenceGenome.gtf -t exon -g gene_id -p -o counts.txt a.bam b.bam c.bam 1.bam 2.bam 3.bam
```

<h3># The parameters in the above example are -a precedes the annotated reference genome in .gtf format, -t for type of data to be analyzed (default is "exon"), -g groups features into metafeatures (with the default being exons grouped into gene identifiers), -p for pair-ended reads, -o precedes the output_file ("counts.txt" in the example), and arguments following the specified output.</h3>

<h3># In the above example, featureCounts will output a dataframe with the file name "counts.txt" with a number of columns equal to the number of samples analyzed, one row for each detected group specified by -g, and the value of each cell equal to the number of times the transcript was detected in the experiment.</h3>
