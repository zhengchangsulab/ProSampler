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

If you want to comple the program, just type:
g++ -o ProSampler.unix ProSampler.cc

If you want to let the program run, do:
chmod +x ProSampler.unix

Now you can run the program "ProSampler" by typing:
./proSampler [options]

As to the two programs, if you type these commands without any input parameter options, you can 
get a list on how to set the parameters.

***************************************************************************************************

Input file:

The following shows the details about parameter specification.

Usage:

./ProSampler -i input_file_name [options]

The input file should be plain TEXT file, rather than WORD or HTML formats. In fact, proSampler 
can recognize restricted FASTA format:
>sequence1 name
ACCCGGTTAACC [sequence 1 as ONE LINE]
>sequence2 name
ACATGTGTGTGA [sequence 2 as ONE LINE]

If you have the following sequence format:
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

you should merge multiple lines belonging to the same sequence into one,
before running ProSampler.

****************************************************************************************************

Description of the optional parameters of ProSampler:

-i	<input file path>
	The name of the input file in FASTA format.

-b	<background file path>
	The background file should also be in FASTA format, same as input file.

-o	<prefix of output files>
	Three files in three types of formats will be outputted after using ProSampler, i.e.
	meme, site and spic formats.
	- meme - The position specific matrices of motifs.
	- site - The binding site information of motifs.
	- spic - The input format for SPIC program used to compare motifs.

-f	<strand flag variable (default: 2)>
	- 1 - Only consider the forward strands of the input sequences.
	- 2 - Consider both forward strands as well as their compplementary strands.

-k	<the length of preliminary motifs (default: 8)>
	The length of k-mers used to identify preliminary motifs.

-l	<the length of the flanking segment lengths used to trim motifs (default: 6)>

-f	<the number of iterations to identify preliminary motifs (default: 100)>
	A number of iterations should be conducted to identify preliminary motifs.

-t	<the cutoff to choose significant k-mers (default: 8.0)>
	Two proportion z-test is used.

-w	<the cutoff to choose subsignificant k-mers (default: 4.5)>
	Two proportion z-test is used.

-z	<the cutoff of two proportion z-test in trimming motif lengths (default: 1.96)>
	Larger cutoff implies higher conservation level.

-c	<the cutoff of Hamming Distance used to merge similar k-mers (default: 1)>

-s	<the cutoff of SW score used to connect nodes in Similarity Graph (default: 1.8)>

-h	<print this message (default: no)>

*****************************************************************************************************

Contact information:

For questions, request and bug reports, please contact:
Yang Li at liyangor@163.com.

******************************************************************************************************
