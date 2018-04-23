#bam_splitNreads.pl

##SYNOPSIS:


	$samtools view -h xx.bam | perl $0 | samtools calmd - xx.reference.fa | samtools sort -o - xx.sort.bam

##Requirements:

	Programs: Perl, samtools

##Descriptions:

	Split CIGAR containing N into separate parts, fields affected:
		FLAG: complementary aplignment will be with 0x800 flag
		POS:  base on CIGAR
		CIGAR:recalculate, introduce H
		TLEN: recalculate
		SEQ:  substring based on CIGAR
		QUAL: substring based on CIGAR
	
	Note: 
		Need to recalculate MD using samtools calmd
		Set \$includingNlen=1 if need to include N length in new CIGAR
		output in sam format

##Example:

	bam_splitNreads.pl xx.bam | samtools calmd -Su - 1AL_v2-ab-k71-contigs.fa.longerthan_200.fa | samtools sort - xx.calmd.st3

##Author:
	Fu-Hao Lu
	Post-Doctoral Scientist in Micheal Bevan laboratory
	Cell and Developmental Department, John Innes Centre
	Norwich NR4 7UH, United Kingdom
	E-mail: Fu-Hao.Lu\@jic.ac.uk

##Copyright

Copyright (c) 2015-2018 Fu-Hao Lu
