# HistoQC
---

HistoQC is an open-source quality control tool for digital pathology slides

![screenshot](https://user-images.githubusercontent.com/9681868/40330248-a39603a2-5d4c-11e8-9d16-cc13fd9e21d4.png)

# Requirements
---

Tested with Python 3.6

Requires:

1. openslide

And the following additional python package: 

1. python-openslide
2. matplotlib
3. numpy
4. scipy
5. skimage
6. sklearn


You can likely install the python requirements using something like (note python 3+ requirement):

pip3 install -r requirements.txt

Openslide binaries will have to be installed separately as per individual o/s instructions

The most basic docker image can be created with the included (7-line) Dockerfile. 

# Basic Usage
---

```  
C:\Research\code\qc>python qc_pipeline.py --help
usage: qc_pipeline.py [-h] [-o OUTDIR] [-p BASEPATH] [-c CONFIG] [-f]
                      [-b BATCH] [-n NTHREADS] [-s]
                      [input_pattern [input_pattern ...]]

positional arguments:
  input_pattern         input filename pattern (try: *.svs or
                        target_path/*.svs ), or tsv file containing list of
                        files to analyze

optional arguments:
  -h, --help            show this help message and exit
  -o OUTDIR, --outdir OUTDIR
                        outputdir, default ./histoqc_output
  -p BASEPATH, --basepath BASEPATH
                        base path to add to file names, helps when producing
                        data using existing output file as input
  -c CONFIG, --config CONFIG
                        config file to use
  -f, --force           force overwriting of existing files
  -b BATCH, --batch BATCH
                        break results file into subsets of this size
  -n NTHREADS, --nthreads NTHREADS
                        number of threads to launch
  -s, --symlinkoff      turn OFF symlink creation

```


Prefered usage is to run from the HistoQC directory, .e.g,:  HistoQC> python qc_pipeline.py -c config.ini -n 4 remote_file_location/*.svs 
(Note: filenames in config.ini are *relative* to directory of execution, unless absolute paths are used)

In case of errors, HistoQC can be run with the same output directory and will begin where it left off, identifying completed images by the presence of an existing directory.
                            
Afterwards, double click index.html to open front end user interface, select the respective results.tsv file from the Data directory

This can also be done remotely, but is a bit more complex, see advanced usage.

# Advanced Usage
---

See [wiki](https://github.com/choosehappy/HistoQC/wiki)


# Citation
---
If you find this software useful, please drop me a line and/or consider citing it:

"HistoQC: An Open-Source Quality Control Tool for Digital Pathology Slides", Janowczyk A., Zuo R., Gilmore H., Feldman M., Madabhushi A., JCO Clinical Cancer Informatics, 2019

Manuscript available [here](http://www.andrewjanowczyk.com/histoqc-an-open-source-quality-control-tool-for-digital-pathology-slides/)
