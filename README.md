## GenoWAP (Deprecated! See [here](https://github.com/rlpowles/GenoWAP-V1.2) for the newest version)

Post-GWAS Prioritization through Integrated Analysis of Functional Annotation

### Dependencies
- [python version >=3.4 or >=2.7,6](https://www.python.org/)
- [requests](http://docs.python-requests.org/en/latest/)
- [progressbar2](https://pypi.python.org/pypi/progressbar2)
- [scipy](http://www.scipy.org)
- [numpy](http://www.numpy.org/)

To install these packages, you can conveniently use **pip**. For example,
```
pip install numpy
```
or 
```
pip install --user numpy
```

### Python2 vs. Python3
prioritize2.py is the python2 compatible version, and prioritize3.py is the python3 version. The latter version has slightly better precision (14 vs 18 digits after decimal point)

### Usage

```
GenoWAP [-h] [-o DESTINATION_PATH] [-b NBINS] [-t THRESHOLD] [-a ANNOTATION_PATH] GWAS_DATA_PATH
```

When ANNOTATION_PATH is not specified, GenoWAP tries to download data from GenoCanyon, and save to file "temp.data" in the current directory.
See `GenoWAP -h` for more detail

### DATA Format
The following format is for both GWAS_DATA and ANNOTATION:

A text file with n lines, each line contains chromosome number, coordinate and the GWAS p-value, separated by one tab (i.e. `'\t'`)

Note: the data given is assumed to contain no duplicated entries. If it does, then the duplicated entries will be ignored during computation and removed from output.

### Build
freeze.py is used for building executables. Please use [cx_Freeze](http://cx-freeze.sourceforge.net/) for the build:

1. Make sure all dependencies are installed for the preferred python version with which you wish to run GenoWAP.

2. Rename the correct python source code to GenoWAP.py

3. Run (where `python` points to the preferred version of python):
```
python freeze.py build
```

The executable will be named `GenoWAP` under the `build` directory.
