# stLFR_read_demux

This repo provides tools for splitting sequencing read data for stLFR (single-tube LFR) by barcodes. 

Input file:
Single-end sequencing read fastq file with barcode sequence appended at the end of each sequence.
Or Pair-end sequencing read fastq files with barcode sequence appended at the end of read2.

Barcode structure:
Each combinatory barcode is consisted of 3 10-base barcode sequence and 2 link sequences.
1. 54 base barcode: 10+6+10+18+10
2. 42 base barcode: 10+6+10+6+10

Output files:
single-end: split_read.fq.gz
Pair-end: split_read.1.fq.gz, split_read.2.fq.gz

In the output fastq files, reads are split by barcodes, as indicated in read names after '#' sign, in the format of [0-9]+_[0-9]+_[0-9]+, each number representing one barcode ID.

To run:

Example: PE100 with 54 base barcodes:

	perl split_barcode_PEXXX_54_reads.1.pl barcode.list barcode_RC.list read_1.fq.gz read_2.fq.gz 100 split_read
	
	perl split_barcode_PEXXX_54_reads.2.pl barcode.list barcode_RC.list read_1.fq.gz read_2.fq.gz 100 split_read
	
Example: SE50 with 42 base barcodes:

	perl split_barcode_SEXXX_42RC_reads.1.pl barcode.list barcode_RC.list read1.fq.gz 50 split_read
