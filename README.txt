Notes by Ziheng
10 October 2017
Edited 22 November 2022

(A) Subsampling 3 sequences per locus for the 3s program

   bpp-subsample-data bpp-subsample-data.ctl 
   bpp-subsample-data bpp-subsample-data.ctl < in-3s-GAR.txt

Input:  bpp-subsample-data.ctl, anopheles.Imap.txt, testdata.coding.3L12.txt
OutputL testdata.coding.3L12.GAR.txt, IDs-GAR.txt

I modified bpp v3 to sample subsets of sequences from the sequence data file for bpp 
for analysis using 3s.  The 3s program uses 3 sequences per locus, of different 
configurations.  This program samples sequences at each locus, with half of the
loci with the configuration 123, a quarter with configuration 113, and another
quarter with configuration 223.  Here 1 2 3 refers to the three species, so 
configuration 123 means one sequence from each species, configuration 113 means 
two sequences species 1 and one sequence from species 3, and so on.  Note that 
species 3 is supposed to be the outgroup.  

The progam was a modification of bpp, originally done to sample the gibbon genomic 
data for Shi & Yang (2018, Mol Biol Evol 35:159-179), and then the anopheles data 
by Thawornwattana et al. (2018 Mol Biol Evol 35:2512-2527).

The original sequence data file coding.3L12.txt has 17027 loci from seven species, but 
i deleted most of the loci and testdata.coding.3L12.txt has only about 10 loci.  
The species are listed in the control file: 
 
  species&tree = 7  G  C  R  L  A  Q  O
                    2  2  2  2  2  2  1

When you run the program and input the indices of the three species, for example 
1 5 3 
which means species G A R, the program will generate a file testdata.coding.3L12.GAR.txt, 
with the species name "GAR" inserted into the file name.  This has the same number of loci 
and with 3 sequences per locus.  The sampled sequence IDs are listed in another file 
IDs-GAR.txt, which you may ignore if it is not useful.


(B) Subsampling 4 sequences per locus for D-statistic, HyDe, etc.

   bpp-subsample-data bpp-subsample-data.ctl 
   bpp-subsample-data bpp-subsample-data.ctl < in-4s-GARO.txt

Input:  bpp-subsample-data.ctl, anopheles.Imap.txt, testdata.coding.3L12.txt, in-4s-GARO.txt
Output: testdata.coding.3L12.GARO.txt, IDs-GARO.txt

Run the command
   bpp-subsample-data bpp-subsample-data.ctl
and type the following input on the monitor:
   4: 1 5 3 7

Or equivalently you can collect the input into a file (in-4s-GARO.txt) and use redirection:

   bpp-subsample-data bpp-subsample-data.ctl < in-4s-GARO.txt

The control file lists 4 species, as follows
  species&tree = 7  G  C  R  L  A  Q  O
                    2  2  2  2  2  2  1

The input (4: 1 5 3 7) means we extrat 4 sequences per locus, one each from G, A, R, O.
The generated sequence file will be in  testdata.coding.3L12.GARO.txt, and the indices
of sequences sampled at each locus are listed in IDs-GARO.txt.
