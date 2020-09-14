# Selection Inference on Short Tandem Repeats (SISTR)
SISTR is a method to measure negative selection at short tandem repeats.  

It takes allele frequency data (per-locus frequencies of each allele length) as input and outputs a posterior estimate of the selection coefficient at each locus.  

For questions on usage, please contact Bonnie Huang (bbhuang@ucsd.edu)

# Dependencies
SISTR uses Python3 and the following libraries: Python Standard Library, SciPy, NumPy.

# Pipeline
1. The first step is a preprocessing step which involves simulating allele frequencies to generate lookup tables used later in SISTR (see step 2).   

   See `simulations/` for further details. 
   
   Example command to run simulations:  
   ```
   python ABC_lookup.py per opt num_sims a_param b_param filenum out_folder use_TMRCA  
   ```
 
   Note: Alternatively, the user can skip this step and use lookup tables already generated for community use: (https://drive.google.com/drive/folders/1g70y6z6sU5DVpF6ZGzosNDVFFoXxnqmn?usp=sharing)

2. The second step is to run SISTR, which requires (1) allele frequency data and (2) precomputed lookup tables generated in step 1. It outputs a posterior estimate of the selection coefficient at each locus with a 95% confidence interval. 

   See `sistr/` for further details.

   Example command to run SISTR:  
   ```
   python SISTR_v1.py \
     --inFile allele_freqs_test.txt \
     --outFile test_results.txt 
   ```

# Folder Contents
* `simulations/`: Contains scripts to generate lookup tables
* `sistr/`: Contains scripts to run SISTR