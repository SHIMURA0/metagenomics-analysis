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

## 1. 创建项目根目录文件夹
在`/data3/prj202x` 路径下新建项目根目录文件，
在
``` bash
bash /home/meta_software/cnas_scripts/V24/cnas_dir.sh GHJCxxx(报告编号)

