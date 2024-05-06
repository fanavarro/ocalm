# CoverageMetric

CoverageMetric is a Python script for measuring the domain coverage of an OWL ontology. It takes an ontology and free text as input, identify the noun phrases in the free text and tries to match them with ontology classes.

## Requirements

This script has been tested by using Python 3.8.19.


## Usage

```
usage: python CoverageMetric.py [-h] --text_folder TEXT_FOLDER --ontology ONTOLOGY
                         [--term_freq_threshold TERM_FREQ_THRESHOLD]
                         --output_prefix OUTPUT_PREFIX [--threads THREADS]

optional arguments:
  -h, --help            show this help message and exit
  --text_folder TEXT_FOLDER
                        Folder containing natural language text files.
  --ontology ONTOLOGY   Ontology file.
  --term_freq_threshold TERM_FREQ_THRESHOLD
                        Threshold to filter the detected noun phrases in the
                        free text based on the noun phrase frequency in the
                        corpus. This threshold is based on the normalized
                        frequency of each term (term frequency / max frequency
                        found), that is from 0 to 1.
  --output_prefix OUTPUT_PREFIX
                        Output prefix to store the results
  --threads THREADS     Threads to use
```

## Outputs

The output consists of 2 files:

  - **text2class.tsv**: shows the best ontology class match for each noun phrase identified in the text files.
  - **class2text.tsv**: shows the best noun phrase match for each ontology class.

Both files show the lexical, semantic, and general score for each match, together with the 10 nearest neighbors found for both the noun phrase extracted from the text files and the ontology class.

## Installation

We recommend to use a virtual environment to execute CoverageMetric.

### Python virtual environment

Some issues when installing the required libraries have been detected when using Python 3.10. If you do not have a Python 3.8 version, please use the conda installation.

Move to the project folder and create a virtual environment:

`python -m venv .venv`

Activate the virtual environment

`source .venv/bin/activate`

Install the required libraries:

`python -m pip install -r requirements.txt`

### Conda virtual environment

Move to the project folder and create the conda environment:

`conda env create -f conda-environment.yaml`

This will have created an environment called *CoverageMetric*. To activate it, use the following command:

`conda activate CoverageMetric`

### Test the application

The following command run the application by using a test ontology and a test text corpus, included within the repository:

`python CoverageMetric.py --text_folder resources/test_text/folder1 --ontology resources/test_ontologies/ontology.owl --output_prefix testCoverageMetricResults/ --threads 8`

If it run successfully, you will see a folder testCoverageMetricResults with the results.