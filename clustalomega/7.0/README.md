# This image belongs to a larger project called Bioinformatics Docker Images Project (http://pegi3s.github.io/dockerfiles)
## (Please note that the original software licenses still apply)

This image facilitates the usage of [Clustal Omega](http://www.clustal.org/omega/), a sequence alignment tool.

# Using the Clustal Omega image in Linux

You should adapt and run the following command: `docker run --rm -v /your/data/dir:/data pegi3s/clustalomega -i /data/sequences.fasta -o /data/sequences_aligned.fasta`

In this command, you should replace:
- `/your/data/dir` to point to the directory that contains the FASTA file you want to align.
- `sequences.fasta` to the actual name of your FASTA file.
- `sequences_aligned.fasta` to the actual name of your aligned FASTA file.

To see the [Clustal Omega](https://www.ebi.ac.uk/seqdb/confluence/display/THD/Clustal+Omega) help, just run `docker run --rm pegi3s/clustalomega --help`.
