

08-08-2024

## This folder contains the steps to run the nf-core-rnaseq pipeline using NEXTFLOWTOWER
## Requirement:  
  -  Must have access to SENSORIUM AWS S3
  -  Must have access to SENSORIUM NEXTFLOWTOWER account

## Step1: In AWS S3: Locate the address of the unprocessed FASTQ files containing the nucleotide sequence data to analyze

   This data is always stored in AWS S3 bucket
   Typically, WUXI data is deposited in s3://cro-wuxi/
              and QUINTARA data is deposited in s3://sensorium-research-rna-seq-raw-quintara/

For this tutorial,we created the folder "TEST"  ---> s3://sensorium-research-rna-seq-raw-quintara/TEST/"
which contains some sample FASTQ files

## Step2:  Create a csv file (FASTQMAP) that maps each samiple ID with the FASTQ addresses corresponding to that sampleID

 The csv file must have the following header: "sample" "fastq_1" "fastq_2" "strandedness"

 sample: sample IDs
 fastq_1 &fastq_2:  are the addresses of the forward/reverse strand
 strandness: this column is filled "reverse"

For an example see: "test.csv"

## Step 3:  Upload the FASTQ-MAP  csv file from STEP 2 into the directory that contains the FASTQ files

 Upload the FASTQ MAP file from STEP 2 into the working directory in STEP1

Here: Create we created: result_TEST

## STEP 3: Create an Output Folder within the "s3://sensorium-tower-bucket" directory 

 Please follow the following format for the folder:
 results_SR_MONTH_DAY_YEAR.

 e.g:  results_SR_05_07_24

For this tutorial, we created the output folder: "result_TEST"

## Step 4: Log into NEXTFLOW TOWER: https://cloud.seqera.io/login 
## Using your sensorium login:

- Click on "LAUNCHPAD" , select "nf-core-rnaseq" then fill out the blank field with the following:
  
Input :  s3://sensorium-research-rna-seq-raw-quintara/TEST/test.csv
Output:  s3://sensorium-tower-bucket/result_TEST/

genome: GRCh37|GRCm38|Rnor_6.0

GRCh37  -----> Human

GRCm38   ----> Mouse

Rnor_6.0  ---> Rat

Note: Leave any other field blank. In this setting the fileds will be auto-populated with the necessary files

## Step5: Click on Launch to start pipeline.
##         Monitor the pipeline under the "RUNS" tab



