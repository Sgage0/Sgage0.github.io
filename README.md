# This repository is my first attempt at sharing example code used for analyzing NGS. The code was run in Linux bash shell and R. I used Subread, which is available through bioconda, and edgeR to analyze
# changes in RNA expression. My practice data set were previously published single-cell transcriptomes, downloaded from the Sequence Read Archive (SRA). I used the Subread/featureCounts function to quantitate
# transcription in Dbp1 knockdown and control murine cells. The function returned a dataframe with several columns, including one column with Gene names and another with ints = the number of transcripts
# detected during sequencing.

# Additionally, edgeR, which I ran using RStudio, was used in the analysis of the knockdown. edgeR output a dataframe of Genes, fold-change (FC) in expression, as well as statistical significance (PValue),
# and false discovery rate (FDR). I then created two lists from the output, knockdown and increased expression, by filtering for PValues <= 0.05, then sorting the output by FC using a basic spread sheet.
# Knockdown was defined as FC < 0.6667 of the control (= 1.5 fold decrease in expression). Increased expression was defined as FC > 1.500 .

# From the three test transcriptomes, three control transcriptomes, and a murine reference genome, featureCounts output six dataframes. Combined, featureCounts detected transcripts for ~10,000 genes; many
# were marginally expressed, while some where strongly expressed. edgeR was able to output a second dataframe, sortable by FC, PValue, and FDR. Nearly half the results were discarded due to high PValue.
# Combining both increased and decreased expression, edgeR determined statistically significant changes in expression of nearly 4,500 transcripts.
