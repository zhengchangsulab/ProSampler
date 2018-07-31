**************************************************************************************************

Overview:

ProSampler
Version 1.0
Release July 18-th, 2018
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
6. README.txt

In additon to your input sequence file, ProSampler needs another file containing background 
sequences that match your input seqeunces. If no background sequences file is available to you, 
ProSampler will generate it by itself.

If you want to compile the ProSampler program, make sure that
ProSampler.cc and Markov.cc are in the current directory, and type 
(suppose you are using a unix plaform):
	
	g++ -o ProSampler.unix ProSampler.cc

and:

	chmod +x ProSampler.unix

Now you can run the program "ProSampler" by typing:
./ProSampler.unix -i input_file [options]

***************************************************************************************************

- input_file - 

The input file should be a plain TEXT file in the FASTA format as either type
or mixed types of the following,
 
< 1 >

	>sequence1 name
	ACCCGGTTAACC [sequence 1 as ONE LINE]
	>sequence2 name
	ACATGTGTGTGA [sequence 2 as ONE LINE]


< 2 >
	>sequence1 name
	ATCTGAATGCA
	AGCTGCACACGTTTTT
	CAGATAAA

	>sequence2 name
	AGTCAGACTACA
	AGCTGCACACTTTT
	CAGATAAA

< 3 >

	>sequence1 name
	AGTCG GTCAC GCACG CACAC
	CGATT CAAAT TGTGA CGACG

	>sequence2 name
	CTCA CTTTTGGG GCATCGAA
	CG  ATTTTACGACC CAGTGG

***************************************************************************************************

If you type the command without any input parameter option, you will
get following Usage information

****************************************************************************************************

Description of the optional parameters of ProSampler:

-i	<input file path>
	Name of the input file in FASTA format.

-b	<background file path>
	Name of the background file in FASTA format, 
	or order of the Markov model to generate background seuquences
	(default: 3, generate background sequences by using 3-rd order Markov model.
	We provide four choices of the order of the Markov Model, i.e. 0, 1, 2, 3.
	The higher the order of the Markov Model, the more consistence between the nucleotide 
	frequencies of input and output sequences.)
	
-d	<the cutoff of Hamming Distance between any two k-mers in a PWM (default: 1)>
	
-o	<prefix of output files>
	Prefix name of the output files in three different formats, i.e.
	meme, site and spic formats.
	- meme - The position specific weight matrices of motifs.
	- site - The binding sites of each motif.
	- spic - The input format for SPIC program used to compare motifs.
	
-m	<number of motifs to be output (default: All)>
    	ProSampler finds all the motifs in the dataset, but the user can 
	choose to output the top n of them.
	
-f	<number of cycles of Gibbs sampling to identify preliminary motifs (default: 100)>
	A number of cycles are needed to identify preliminary motifs.	

-k	<length of preliminary motifs (default: 8)>
	The length of k-mers used to identify preliminary motifs.

-l	<length of the flanking l-mers to extend the preliminary motifs (default: 6)>

-c	<cutoff of Hamming distance to merge similar k-mers (default: 1)>

-r	<cutoff of Hamming distance to delete redundant motifs based on consensus sequences (default: 1)>

-p	<number (1 or 2) of strands to be considered (default: 2)>
	- 1 - Only consider the forward strand of the input sequences.
	- 2 - Consider both the forward and reverse compplementary strands. 
	
-t	<cutoff of z-value to choose significant k-mers (default: 8.0)>
	A higher z-value cutoff for two-proportion z-test.

-w	<cutoff of z-value to choose subsignificant k-mers (default: 4.5)>
	A lower z-value cutoff for two-proportion z-test

-z	<cutoff of z-value to extend preliminary motif lengths (default: 1.96)>
	A larger cutoff implies higher conservation level.

-s	<cutoff of SW score used to connect nodes in the motif similarity graph (default: 1.8)>

-h	<print this message (default: no)>

*****************************************************************************************************

Contact information:

For questions, request and bug reports, please contact:
Yang Li at liyangor@163.com.

******************************************************************************************************
