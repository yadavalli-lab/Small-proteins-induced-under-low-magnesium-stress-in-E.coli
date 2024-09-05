# Small-proteins-induced-under-low-magnesium-stress

This repository contains the code and associated files for the study titled "Investigation of small proteins induced under magnesium starvation reveals a novel connection among three signaling systems in _E. coli_," currently available on _bioRxiv_ ([link to paper](#)).

## Repository Organization

The repository is structured into folders with self-descriptive names to facilitate navigation and understanding of the project workflow:

- `code`: Contains the code used for data processing, analysis, and figure generation.
- `data_frames`: Holds various data files created or used during the analysis.
- `seqdata`: Raw and processed sequencing data organized by analysis type (e.g., RNA-Seq, Ribo-RET).
- `alignment`: Contains alignment results and indices for tools like HISAT2 and Kallisto.
- `figures`: Includes figures generated from the analysis.

**Note:** Large files, such as raw sequencing data and some processed data files, are managed with Git LFS due to their size. These files are not directly stored in the repository but are tracked and downloaded separately using LFS. To fully clone the repository with all the large files, ensure that Git LFS is installed and set up on your system.

## Hardware and Software Information

**Hardware:**
- **CPUs**: 2 Intel Xeon CPU E5-2660 v4 @ 2.00GHz, each with 14 cores and 2 threads per core, totaling 56 threads.
- **RAM**: 264 GB
- **Operating System**: Ubuntu 18.04.6 LTS

**Software Versions:**
| Software      | Version   |
|---------------|-----------|
| cutadapt      | 3.5       |
| python        | 3.6.9     |
| hisat2        | 2.2.1     |
| kallisto      | 0.48.0    |
| samtools      | 1.16.1    |
| UMI-tools     | 1.1.2     |
| fastp         | 0.23.2    |
| R             | 4.2.3     |

### Additional Information:

When knitted to an HTML, each R Markdown (**`Rmd`**) document will display the versions of the packages used at the bottom, ensuring reproducibility. Many steps in the analysis can utilize multiple threads to speed up processing, although this is optional. If needed, you can adjust the thread usage; the only impact will be increased runtime.

**Phases of the Analysis:**
1. Sequencing Data Processing: Processes the raw sequencing data to prepare it for alignment and quantification.

2. Analysis: Executes various analyses based on the processed sequencing data.

3. Interpretation: Creates visualizations of the data generated during the analysis phase.


## Directory Structure

1. Ribo-RET Directory Structure
```plaintext
.
├── alignment
│   └── hisat2
│       ├── indices
│       ├── output2
│       └── output_dedup
├── code
│   ├── analysis
│   ├── data_processing
│   └── figures
├── dataframes
├── fastas
├── figures
├── gffs
└── seqdata
    ├── 1-original
    ├── 2-adapter_removed_demux
    ├── 3-umi_extracted
    ├── 4-rtrna_depleted
```
### Notes on Directory Structure and Files:
- `output2`: Contains reads that have not been deduplicated.
- `output_dedup`: Contains deduplicated reads. Use this directly for downstream analysis. 
- `adapter_removed_demux` (GSE276379): These files are adapter-removed and demultiplexed. After this step, the reads should proceed through the following stages:
  - `UMI Extraction`: Extract unique molecular identifiers from the reads.
  - `rtRNA Depletion`: Remove ribosomal RNA sequences.
  - `Mapping`: Align the reads to the reference genome using HISAT2.
  - `Deduplication`: Remove duplicate reads to finalize the data for downstream analysis.

2. RNA-Seq Directory Structure
```plaintext
.
├── alignment
│   └── kallisto
│       ├── indices
│       └── output
├── code
│   ├── analysis
│   ├── data_processing
│   └── figures
├── dataframe
├── fasta
├── figures
├── gffs
├── reports
└── seqdata
    ├── 1-original
    └── 2-cleaned
```
### Notes on Directory Structure and Files:
- `output`: This folder contains reads that have been mapped to the transcriptome using Kallisto.
- `2-cleaned` (GSE276379): These are the demultiplexed reads. After this step, the reads should proceed through the following stage:
  - `Mapping`: Align the reads to the reference transcriptome using Kallisto.

3. Other Analysis Directory Structure
```plaintext
.
├── other_analysis
│   ├── codes
│   ├── dataframe
│   └── figures
```
### Notes on Directory Structure and Files:
- `codes`: This folder contains scripts specifically related to the analysis and generation of figures referenced in the paper, identified by their figure numbers.
- `dataframe`: Contains data files that are used for the respective figures, matching the data used in the analysis scripts.
- `figures`: Stores the generated figures, each named according to its respective figure number from the paper.

  
