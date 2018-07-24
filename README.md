**************************************************************************************************

Overview:

ProSampler
Version 1.0
Release July 12-th, 2018
An ultra-fast motif finding program on large ChIP-seq datasets

Reference
Li Y#, Ni P#, Zhang S, Li G, Su Z*. Ultra-fast and accurate motif finding in large ChIP-seq datasets
 reveals transcription factor binding patterns.

ProSampler is free to academia. Please do not distribute the executable of the program to others 
without a license or consent of the owners. For details about obtaining this program, please refer 
to https://github.com/zhengchangsulab/prosampler.

**************************************************************************************************

Start using ProSampler:

Once you download and unzip PROSAMPLER.tar.gz, you will see several files:
1. ProSampler.cpp
2. ProSampler.unix
3. ProSampler.maxos
4. ProSampler.exe
5. README.txt

In the following context, we use ProSampler.unix as an example.

If you want to compile the program, just type:
g++ -o ProSampler.unix ProSampler.cc

If you want to run let the program, type:
chmod +x ProSampler.unix

Now you can run the program "ProSampler" by typing:
./proSampler [options]

If you type the command without any input parameter option, you will
get a menue of how to set the parameters.

***************************************************************************************************

Input file:

The following shows the details about parameter specification.

Usage:

./ProSampler -i input_file_name [options]

The input file should be a plain TEXT file in FASTA format as follows,  
>sequence1 name
ACCCGGTTAACC [sequence 1 as ONE LINE]
>sequence2 name
ACATGTGTGTGA [sequence 2 as ONE LINE]

If you have the following sequences in multiple lines as follows, 
>seq1
ATCTGAATGCA
AGCTGCACACGTTTTT
CAGATAAA

>seq2
AGTCAGACTACA
AGCTGCACACTTTT
CAGATAAA

>seq3
1 AGTCG GTCAC GCACG CACAC 20
21 CGATT CAAAT TGTGA CGACG 40

you should merge multiple lines belonging to the same sequence into one, before running ProSampler.

****************************************************************************************************

Description of the optional parameters of ProSampler:

-i	<input file path>
	The name of the input file in FASTA format.

-b	<background file path>
	The background file should also be in FASTA format, same as input file.

-o	<prefix of output files>
	Motifs will be output three different formats in in three files, i.e.
	meme, site and spic formats.
	- meme - The position specific weight matrices of motifs.
	- site - The binding sites of each motif.
	- spic - The input format for SPIC program used to compare motifs.

-f	<strand flag variable (default: 2)>
	- 1 - Only consider the forward strands of the input sequences.
	- 2 - Consider both forward and reverse compplementary strands.

-k	<the length of preliminary motifs (default: 8)>
	The length of k-mers used to identify preliminary motifs.

-l	<the length of the flanking segment lengths used to extend the motifs (default: 6)>

-f	<the number of cycles Gibis sampling to identify preliminary motifs (default: 100)>
	A number of iterations is needed to identify preliminary motifs.

-t	<the cutoff to choose significant k-mers (default: 8.0)>
	A higher z-value cutoff for two proportion z-test.

-w	<the cutoff to choose subsignificant k-mers (default: 4.5)>
	A lower z-value cutoff for two proportion z-test

-z	<the cutoff of two proportion z-test in extending motif lengths (default: 1.96)>
	A larger cutoff implies higher conservation level.

-c	<the cutoff of Hamming Distance used to merge similar k-mers (default: 1)>

-s	<the cutoff of SW score used to connect nodes in Similarity Graph (default: 1.8)>

-h	<print this message (default: no)>

*****************************************************************************************************

Contact information:

For questions, request and bug reports, please contact:
Yang Li at liyangor@163.com.

******************************************************************************************************
