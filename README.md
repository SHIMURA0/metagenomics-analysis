# 宏基因组分析

## 完整项目文件架构
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
      ├── ${sample_id}_1.fastqc.zip
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
  ├── prodigal_temp/
  ├── removelow/
  ├── removelow_qc/
  ├── salmon_temp/
  ├── temp_bam/
  ├── temp_bamsort/
  ├── tmp/
  ├── Unigenes/
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

























  


  ├── utils.py ├── data/ │ ├── input/ │ │ ├── data_file_1.csv │ │ ├── data_file_2.csv │ ├── output/ │ ├── results.csv ├── tests/ │ ├── test_main.py │ ├── test_utils.py ├── README.md ├── requirements.txt
```

## 1. 创建项目根目录文件夹
在`/data3/prj202x` 路径下新建项目根目录文件，
在
``` bash
bash /home/meta_software/cnas_scripts/V24/cnas_dir.sh GHJCxxx(报告编号)

