<h4># As part of my training with featureCounts and NGS .sam data, I used previously published sequences uploaded to the SRA website. These data are frequently also hosted on AWS, but the SRA website offers access to the data for free without requiring payment or creating an account. In fact, I highly recommend samtools and sra-tools, both of which are available from bioconda.</h4>

<h4># In order to download this data and convert it into usable .bam format, I downloaded and installed sra-tools (https://anaconda.org/bioconda/sra-tools) and samtools (https://anaconda.org/bioconda/samtools) for bioconda.</h4>

<h4># Once installed, downloading the data sets is not difficult, but it can be time consuming. The NGS data sets I used averaged nearly 3 GB each; using residential internet, it took most of a day to download sixe of these files from the SRA database.</h4>

<h4># In my "Lab" environment in bioconda, I used the following commands to download the files:</h4>

```
sam-dump SRR11111111 | samtools view -bS - > 1.bam
```

<h4># Where "SRR11111111" is an example name for data available to download from the SRA website (presumably sequence data is always an eight-digit number prefixed with SRR), and "1.bam" is the name of the destination for the downloaded data.</h4>

<h4># The first command, sam-dump, downloads the file from the SRA website. SRA keeps the file in an easy-to-read .sam format, but we need the binary format, .bam, to run our analysis. Therefore, I immediately piped the output inline from the download command to the samtools view command. The two arguments, "-b" and "-S", indicate the .bam output and the .sam input, respectively, and the "- >" argument labels "1.bam" as the destination for the reformatted .sam data.</h4>
