# RepetitiveRegion_Knowledge
[Difference between hg38.fa.gz and GCA_000001405.15_GRCh38_full_analysis_set.fna.gz](https://groups.google.com/a/soe.ucsc.edu/g/genome/c/RI7uDc7oG80) 

[BWA-MEM and repetitive genomes](https://www.reddit.com/r/bioinformatics/comments/12seubs/bwamem_and_repetitive_genomes/) 
* reads align more than one region receive low MAPQ score
* align to the whole reference including repetitive regions (i.e. no masking) and then filter out poor quality alignments post hoc

[SAM](https://samtools.github.io/hts-specs/SAMv1.pdf)

[bwa mem and multiply mapped reads](https://www.biostars.org/p/304614/)
* When a read matches in its entirety, with an equal score in multiple locations, one of the locations is picked at random, is labeled as primary, will be given a mapping quality of zero and will have an XA tag that contains the alternative locations (this is identical to how bwa aln worked)
* When different, non-overlapping regions of a read align with high scores to different, non-linear locations in the genome, the higher score alignment will be labeled as primary, the others may be reported as secondary alignments. There is some threshold on how many of these secondary alignments will be reported (bwa aln did not produce secondary alignments)
* When complementary regions of a read (the pieces add up to the full read) align to different, non-linear genomic locations, with no little to no overlap, one of the alignments will be labeled as primary, the others as supplementary alignments (bwa aln did not produce supplementary alignments)
