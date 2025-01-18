# 宏基因组分析

## 宏基因组分析
```markdown 
version: 1.0
author: jing liu
duration: 3 months
```

### 完整项目文件架构
``` 
project_root/
  ├── sample_name.txt
  ├── rename1.txt
  ├── rename2.txt
  ├── rename.txt
  ├── CNASrun.log
  ├── 01.QC_reads/
      ├── raw_qc_count.txt
      ├── raw_qc.html
      ├── raw_qc_data/
          ├── multiqc_data.json
          ├── multiqc_fastqc.txt
          ├── multiqc_general_stats.txt
          ├── multiqc.log
          ├── multiqc_sources.txt
      ├── clean_qc_count.txt
      ├── clean_qc.html
      ├── clean_qc_data/
          ├── multiqc_data.json
          ├── multiqc_fastqc.txt
          ├── multiqc_general_stats.txt
          ├── multiqc.log
          ├── multiqc_sources.txt
  ├── Q2.cleandata/
      ├── ${sample_id}_1.fq.gz
      ├── ${sample_id}_2.fq.gz
  ├── Q3.assembly/
      ├── ${sample_id}.contigs.fa
      ├── unmapped_reads_summary.txt
  ├── Q4.quast_re/
      ├── contigs.txt
      ├── contigs.txt_allcontigs.png
      ├── contigs.txt_GC.png
      ├── contigs.txt_N50.png
      ├── contigs.txt_totallength.png
      ├── ${sample_id}/
  ├── Q5.Unigenes/
      ├── Class.txt
      ├── Family.txt
      ├── formatTaxa.txt
      ├── Genus.txt
      ├── Order.txt
      ├── ORF_stats.txt
      ├── Phylum.txt
      ├── Species.txt
      ├── Summary_Annotation.txt
      ├── Unigenes.fa
      ├── Unigenes_stats.txt
      ├── Unigenes.TPM
      ├── normalized/
          ├── Class.txt
          ├── Family.txt
          ├── Genus.txt
          ├── Order.txt
          ├── Phylum.txt
          ├── Species.txt
          ├── Summary_Annotation.txt
  ├── raw_qc/
      ├── ${sample_id}_1_fastqc.html
      ├── ${sample_id}_1_fastqc.zip
      ├── ${sample_id}_2_fastqc.html
      ├── ${sample_id}_2_fastqc.zip
  ├── raw_fq/
      ├── ${sample_id}_1.fq.gz
      ├── ${sample_id}_2.fq.gz
  ├── ref/
      ├── genome/
      ├── index/
  ├── clean_qc/
      ├── ${sample_id}_1.fastqc.html
      ├── ${sample_id}_1.fastqc.zip
      ├── ${sample_id}_2.fastqc.html
      ├── ${sample_id}_2.fastqc.zip
  ├── dmnd_NR/
  ├── fastp_file/
      ├── fastp.html
      ├── fastp.json
  ├── megantaxa/
  ├── ORF_result/
      ├── rename.txt
      ├── ${sample_id}.fa
      ├── Unigenes.fa
  ├── prodigal_temp/
      ├── bbmapOut/
          ├── ORFgenestats.txt
          ├── ${sample_id}genesMapreadsl.txt
          ├── ${sample_id}genestats.txt
          ├── ${sample_id}mapped.sam
          ├── ${sample_id}mapped.sorted.sam
          ├── ${sample_id}mapped.sorted.sam.bai
      ├── filter/
          ├── ${sample_id}.fa
      ├── ${sample_id}.fa
      ├── ${sample_id}.gff
  ├── removelow/
      ├── ${sample_id}_1.fq.gz
      ├── ${sample_id}_2.fq.gz
  ├── removelow_qc/
      ├── ${sample_id}_1.fastqc.html
      ├── ${sample_id}_1.fastqc.zip
      ├── ${sample_id}_2.fastqc.html
      ├── ${sample_id}_2.fastqc.zip
      ├── removelow_qc.html
      ├── removelow_qc_data/
          ├── multiqc_data.json
          ├── multiqc_fastqc.txt
          ├── multiqc_general_stats.txt
          ├── multiqc.log
          ├── multiqc_sources.txt
  ├── salmon_temp/
      ├── index/
      ├── ${sample_id}quant/
  ├── temp_bam/
      ├── contigs_map_reads/
      ├── ${sample_id}_mapped.bam
  ├── temp_bamsort/
      ├── contigs_map_reads/
          ├── ${sample_id}_unmappedsorted_reads.bam
      ├── ${sample_id}_unmapped_sorted.bam
  ├── tmp/
      ├── 15012646679834680840/
      ├── latest/
  ├── Unigenes/
      ├── DB
      ├── DB.dbtype
      ├── DB_h
      ├── DB_h.dbtype
      ├── DB_h.index
      ├── DB.index
      ├── DB.lookup
      ├── DB.source
  ├── cluster_run.out
  ├── contigs_map_reads.out
  ├── genes_taxa.out
  ├── magahit_run.out
  ├── ORFlist.txt
  ├── ORF_run.out
  ├── quast_run.out
  ├── readsqc1.out
  ├── readsqc3.out
  ├── removehost_run1.out
  ├── salmon_run.out
  ├── Unigenesclu_seq.fasta
  ├── Unigenes_clustered.tsv
  ├── UnigenesDB_clu.0
  ├── UnigenesDB_clu.1
  ├── ...
```

### Step 1. Iniating the new project

1.1 Create the project root directory using the following shell (bash) script
```bash
mkdir /data3/proj${year}/GHJC${year}${month}${date}${index}R${index}
```
1.2 Create two text file 
```markdown
projectInfo.txt
sample_name.txt
```

### Step 2. Formatting fastq files

2.1. Create a new directory for raw fastq file using the following shell (bash) script
```bash
mkdir /projectRoot/raw_fq
```
2.2. Create rename.txt file  
2.3. Renaming file using the following shell (bash) script 
```bash
ls -l raw_fq/ | sed '1d' | sed -r 's/(.*)([[:space:]])(.*)/\2/' > rename1.txt
```
```bash
cat rename1.txt | awk -F '-' '{print $3"_"$6}' | awk -F '_' '{print $1"_"$4}' > rename2.txt
```
2.4 Check if the number of rows of rename2.txt is twice as the number of rows of sample_name.txt using the following shell (bash) script
```bash
lines_rename2=$(wc -l < rename2.txt); lines_sample_name=$(wc -l < sample_name.txt); if [ "$lines_rename2" -eq $((2 * lines_sample_name)) ]; then echo "rename2.txt 的行数是 sample_name.txt 的两倍"; else echo "rename2.txt 的行数不是 sample_name.txt 的两倍"; fi
```
2.5. Renaming the raw fastq file
```bash
cd raw_fq/
bash /home/meta_software/cnas_scripts/V24/rawfq_rename.sh ../rename.txt
```

### Step 3. Data analysis

#### Step 3.1. Preparing environments, files and folders
3.1.1. Activating conda environment
```bash
conda activate meta1_py3
```
3.1.2. Creating a directory for intermediate results.
```bash
bash /home/meta_software/cnas_scripts/V24/cnas_dir.sh GHJC${report_id}
```
#### Step 3.2. Raw data quality checking and cleaning 

3.2.1. Using FastQC and MUltiQC for generating quality checking report for raw sequencing data 
```bash
nohup bash /home/meta_software/cnas_scripts/V24/readsqc1.sh /projectRoot/sample_name.txt > readsqc1.out 2>&1 &
```
outputFile: 
```markdown
projectRoot/removelow/fq.gz
```

3.2.2. Removing human genes using Bowtie2
```bash
nohup bash /home/meta_software/cnas_scripts/V24/removehost_run1.sh /projectRoot/sample_name.txt > removehost_run1.out 2>&1 &
```
3.3.3. Generating raw qc count and clean qc count files.
```bash
nohup bash /home/meta_software/cnas_scripts/V24/readsqc3.sh > readsqc3.out 2>&1 &
```
outputFile: 
```markdown
01.QC_reads/raw_qc_count.txt
01.QC_reads/clean_qc_count.txt
```




















  
```

## 1. Make new directory for project 
在`/data3/prj${year}` 路径下新建项目根目录文件，
Use the following shell (bash) script to create the new report project root dirtectory 
``` bash
bash /home/meta_software/cnas_scripts/V24/cnas_dir.sh GHJC${report_id}

