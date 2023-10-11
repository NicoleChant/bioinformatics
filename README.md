# Challenges


## Prep

You can clone this repo by running

```
git clone git@github.com:NicoleChant/Z-DNA.git 
```


## Fasta files

Inside the data directory there is a fasta file. 

Fasta files are a data storage format that are composed of chromosomes and their associate nucleotide sequences. 
Normally, it's chromosome starts with the '>' symbol and to line below the nucleotide corresponding to this chromosome is
presented.

```
>ChromosomeI
AGCATGAGAGAGGCGCGGAGAGAGCGGCGCGAGCAGA
>ChromosomeII
AGGGAGCGCGCGAGAGGNGAGAGCGGCGCGAGGNNGA
```

There are four nucleotides A, G, C, T but sometimes we may encounter N inside the nucleotide sequence. N is equivalent to unknown.


## Challenges

You need to create a script to read it and answer (by using Python!) the following questions:

- How many chromosomes exist in the fasta file?
- Count all the trinucleotides that appear in the fasta file. Which are the top 10 in counts?
- (Bonus) Create a barplot to display that information.
- Calculate the most frequent dinucleotide across the whole file.
- Calculate the most frequent dinucleotide under each chromosome and compare it with the most frequent globally. What do you notice?



## Help

You will have to use the `open` function to read a file. A simple way to do it:

```
fasta_lines # a list where we will store each line
with open(<filename>, mode='r') as f:
    # After the for loop our list should contain all the lines of the fasta file
    for line in f:
        fasta_lines.append(line)
```

Normally, we do not want to reinvent the wheel so in programming we tend to use libraries other people made.
In our case, an excellent choice to read and parse a fasta file would be to use biopython, a Python module 
which helps us accomplish bioinformatics tasks.


Let's install some important packages

```
pip install biopython
```

To read the fasta file you may want to use the following function:


```
from Bio import SeqIO

def read_fasta(file_path):
    records = []
    for record in SeqIO.parse(file_path, 'fasta'):
        records.append((str(record.id), str(record.seq)))
    return records
```
