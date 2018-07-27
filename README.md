**************************************************************************************************

Overview:

ProSampler
Version 1.0
Release July 12-th, 2018
An ultra-fast motif finding program in large ChIP-seq datasets

Reference
Li Y, Ni P, Zhang S, Li G, Su Z. Ultra-fast and accurate motif finding in large ChIP-seq datasets
 reveals transcription factor binding patterns.

ProSampler is free to academia. Please do not distribute the executable of the program to others 
without a license or consent of the owners. For details about obtaining this program, please refer 
to https://github.com/zhengchangsulab/prosampler.

**************************************************************************************************

To use ProSampler, download and unzip PROSAMPLER.tar.gz, and you will see the following files:

1. ProSampler.cc
2. ProSampler.unix
3. ProSampler.macos
4. ProSampler.exe
5. Markov.cc
6. Markov.unix
7. Markov.macos
8. Markov.exe
9. README.txt

In additon to your input sequence file, ProSampler needs another file containing background sequences that match your input seqeunces. If no background sequences file is available to you, we provide a program Markov to generate the background sequences file.

If you want to compile the Markov program, just type (suppose you are using a unix plaform):
g++ -o Markov.unix Markov.cc

and:
chmod +x Markov.unix

Now you can run the program "Markov" by typing:
./Markov.unix [options]

If you type the command without any input parameter option, you will
get following Usage information:

***************************************************************************************************

Usage:

./Markov -i input_file_name -b output_file_name -f order_of_markov_model

- input_file - 

The input file should be a plain TEXT file in the FASTA format as follows,  
>sequence1 name
ACCCGGTTAACC [sequence 1 as ONE LINE]
>sequence2 name
ACATGTGTGTGA [sequence 2 as ONE LINE]

If your sequences are listed in multiple lines as follows, 
>seq1
ATCTGAATGCA
AGCTGCACACGTTTTT
CAGATAAA

>seq2
AGTCAGACTACA
AGCTGCACACTTTT
CAGATAAA

>seq3
AGTCG GTCAC GCACG CACAC
CGATT CAAAT TGTGA CGACG

you need to merge the lines belonging to the same sequence into one, before running Markov.

- output file -

The output file has the same format as that of the input file.

- order_of_markov_model -

We provide four choices of the order of the Markov Model, i.e. 0, 1, 2, 3.
The higher the order of the Markov Model, the more consistence between the nucleotide frequencies of input and output sequences.

***************************************************************************************************

The ProSampler program can be similarly compiled as the Markov program. ProSampler requirs the sequences files in the same format as does Markov.

****************************************************************************************************

Description of the optional parameters of ProSampler:

-i	<input file path>
	Name of the input file in FASTA format.

-b	<background file path>
	Name of the background file in FASTA format.
	
-d  <Number of degenerate positions in a PSM>
	
-o	<prefix of output files>
	Prefix name of the output files in three different formats, i.e.
	meme, site and spic formats.
	- meme - The position specific weight matrices of motifs.
	- site - The binding sites of each motif.
	- spic - The input format for SPIC program used to compare motifs.
	
-m  <n, number of motifs to be output (default: All)>
    ProSampler finds all the motifs in the dataset, but the user can choose to output the top n of them.
	
-f	<number of cycles of Gibbs sampling to identify preliminary motifs (default: 100)>
	A number of cycles are needed to identify preliminary motifs.	

-k	<length of preliminary motifs (default: 8)>
	The length of k-mers used to identify preliminary motifs.

-l	<length of the flanking l-mers to extend the preliminary motifs (default: 6)>

-c	<cutoff of Hamming distance to merge similar k-mers (default: 1)>

-r	<cutoff of Hamming distance to delete redundant motifs based on consensus sequences (default: 1)>

-p  <number (1 or 2) of strands to be considered (default: 2)>
	- 1 - Only consider the forward strand of the input sequences.
	- 2 - Consider both the forward and reverse compplementary strands. 
	
-t	<cutoff of z-value to choose significant k-mers (default: 8.0)>
	A higher z-value cutoff for two-proportion z-test.

-w	<cutoff of z-value to choose subsignificant k-mers (default: 4.5)>
	A lower z-value cutoff for two-proportion z-test

-z	<cutoff of z-value to extend preliminary motif lengths (default: 1.96)>
	A larger cutoff implies higher conservation level.

-s	<cutoff of SW score used to connect nodes in thhe motif similarity graph (default: 1.8)>

-h	<print this message (default: no)>

*****************************************************************************************************

Contact information:

For questions, request and bug reports, please contact:
Yang Li at liyangor@163.com.

******************************************************************************************************
