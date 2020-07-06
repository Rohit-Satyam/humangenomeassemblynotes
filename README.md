# humangenomeassemblynotes

Aligning the reads using bowtie2

    bowtie2 --fast-local -p 1 -q -I -X -x -1 -2 -fr

```
-I/--minins <int>
The minimum fragment length for valid paired-end alignments. E.g. if  `-I 60`  is specified and a paired-end alignment consists of two 20-bp alignments in the appropriate orientation with a 20-bp gap between them, that alignment is considered valid (as long as  [`-X`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-X)  is also satisfied). A 19-bp gap would not be valid in that case. If trimming options  [`-3`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-3)  or  [`-5`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-5)  are also used, the  [`-I`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-I)  constraint is applied with respect to the untrimmed mates.

The larger the difference between  [`-I`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-I)  and  [`-X`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-X), the slower Bowtie 2 will run. This is because larger differences between  [`-I`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-I)  and  [`-X`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-X)  require that Bowtie 2 scan a larger window to determine if a concordant alignment exists. For typical fragment length ranges (200 to 400 nucleotides), Bowtie 2 is very efficient.

Default: 0 (essentially imposing no minimum)

-X/--maxins <int>

The maximum fragment length for valid paired-end alignments. E.g. if  `-X 100`  is specified and a paired-end alignment consists of two 20-bp alignments in the proper orientation with a 60-bp gap between them, that alignment is considered valid (as long as  [`-I`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-I)  is also satisfied). A 61-bp gap would not be valid in that case. If trimming options  [`-3`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-3)  or  [`-5`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-5)  are also used, the  `-X`  constraint is applied with respect to the untrimmed mates, not the trimmed mates.

The larger the difference between  [`-I`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-I)  and  [`-X`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-X), the slower Bowtie 2 will run. This is because larger differences between  [`-I`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-I)  and  [`-X`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-X)  require that Bowtie 2 scan a larger window to determine if a concordant alignment exists. For typical fragment length ranges (200 to 400 nucleotides), Bowtie 2 is very efficient.

Default: 500.

--fr/--rf/--ff

The upstream/downstream mate orientations for a valid paired-end alignment against the forward reference strand. E.g., if  `--fr`  is specified and there is a candidate paired-end alignment where mate 1 appears upstream of the reverse complement of mate 2 and the fragment length constraints ([`-I`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-I)  and  [`-X`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-X)) are met, that alignment is valid. Also, if mate 2 appears upstream of the reverse complement of mate 1 and all other constraints are met, that too is valid.  `--rf`  likewise requires that an upstream mate1 be reverse-complemented and a downstream mate2 be forward-oriented.  `--ff`  requires both an upstream mate 1 and a downstream mate 2 to be forward-oriented. Default:  `--fr`  (appropriate for Illumina’s Paired-end Sequencing Assay).

--fast-local

Same as:  `-D 10 -R 2 -N 0 -L 22 -i S,1,1.75`

-q

Reads (specified with  `<m1>`,  `<m2>`,  `<s>`) are FASTQ files. FASTQ files usually have extension  `.fq`  or  `.fastq`. FASTQ is the default format. See also:  [`--solexa-quals`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-solexa-quals)  and  [`--int-quals`](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#bowtie2-options-int-quals).

-x <bt2-idx>

The basename of the index for the reference genome. The basename is the name of any of the index files up to but not including the final  `.1.bt2`  /  `.rev.1.bt2`  / etc.  `bowtie2`  looks for the specified index first in the current directory, then in the directory specified in the  `BOWTIE2_INDEXES`  environment variable.

-1 <m1>

Comma-separated list of files containing mate 1s (filename usually includes  `_1`), e.g. `-1 flyA_1.fq,flyB_1.fq`. Sequences specified with this option must correspond file-for-file and read-for-read with those specified in  `<m2>`. Reads may be a mix of different lengths. If  `-`  is specified,  `bowtie2`  will read the mate 1s from the “standard in” or “stdin” filehandle.

-2 <m2>

Comma-separated list of files containing mate 2s (filename usually includes  `_2`), e.g. `-2 flyA_2.fq,flyB_2.fq`. Sequences specified with this option must correspond file-for-file and read-for-read with those specified in  `<m1>`. Reads may be a mix of different lengths. If  `-`  is specified,  `bowtie2`  will read the mate 2s from the “standard in” or “stdin” filehandle.
```
