# AlignmentUtilis

`AlignmentUtilis` is a collection utilities of sequence alignment algorithms,

- Needleman-Wunsch and Smith-Watermen algorithms to conduct sequence alignment with affine gap penalty
- Naive exact matching to conduct reads alignment problem
- ...

## How to get it?

```shell
pip install AlignmentUtilis
```



## How to use it?

```shell
# 1. PairwiseSequenceAlignment
from AlignmentUtilis.Pairwise import *
# Test
seq1 = "TCGTAGACGA"
seq2 = "ATAGAATGCGG"
# Run Global Alignment
PairwiseSequenceAlignment.Runalignment(seq1, seq2, 1, -1, -2, -1, local=False)
# Run Local Alignment
PairwiseSequenceAlignment.Runalignment(seq1, seq2, 1, -1, -2, -1, local=True)

# 2. Naive exact matching
from AlignmentUtilis.Naive import *
# Naive Exact Macthing Basic Utility Test
test_occurrences = Naive.naive_exact_matching('AG', 'AGCTTAGATAGC')
print('The pattern is AG')
print('The target sequence is AGCTTAGATAGC')
print(f'The start position of exact matching is {test_occurrences}')

# 3. Booyer-Moore algorithm to reduce the unnecessary alignments
from AlignmentUtilis.BM import *
# BoyerMoore Test
p = 'TCAA'
p_bm = BoyerMoore(p)
print(p_bm.amap)
print(p_bm.bad_character_rule(2, 'T'))
# boyer_moore Test
t = 'ACGTCGTGCGGTGAGTCGGTAGCGTAGCTAGATACAATCAAGAGAGAGTGCGGAGTGCGAGTCAA'
occurrences = boyer_moore(p, p_bm, t)
print(occurrences)

# 4. Kmer indexing of target sequence, and simple application of query sequence alignment
from AlignmentUtilis.KmerIndex import *
t = 'GCTACGATCTAGAATCTA'
p = 'TCTA'
index = Index(t, 2)
print(queryIndex(p, t, index))
```



## License

MIT License
Copyright (c) 2022 Youpu Chen
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.