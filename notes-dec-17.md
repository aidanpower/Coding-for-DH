# Coding for the Digital Humanities: Problem Solving

December 17th, 2024

- [Website link](https://dh-coding-docs.netlify.app/)
- [Home](README.md)
- [Code](coding-for-dh.ipynb)

## Stopword Errors

Fixed the issue I was having with the quotations by listing them in double quotations in the extended stopwards list:

```
stop_words.extend(["n't", "'s", 'would', '—', "“", "”", '"'])
```

## Langauges

I received an email from Library Technology Services confirming that the non-English articles were appearing due to a lack of information in Omni's database and English being the assumed default. I used the [langdetect](https://pypi.org/project/langdetect/) python package to fill in the empty language column in the dataframe and counted them as shown below:

| Language | Count |
| :---: | :---: |
| English | 29 |
| Italian | 4 |
| Danish | 3 |
| Spanish | 2 |
| Portuguese | 1 |
| German | 1 |

## Output

Of the 50 articles I downloaded, I removed 10 with no abstract and another 11 for not being written in English. The resulting dataframe of English only artilces with publication year added can be found [here](DH-lit-review-output.csv).

## Cleaned Word Frequency

```
Abstract frequency distribution
95: humanities
90: digital
56: research
42: dh
26: analysis
25: field
24: topic
24: text
23: study
19: new
19: reading
18: work
18: data
18: texts
16: also
15: studies
15: dhp-lclw
14: paper
13: topics
13: exploration
```
```
Stemmed frequency distribution
101: human
92: digit
59: research
42: dh
42: text
39: studi
37: topic
32: explor
32: use
26: field
26: analysi
21: read
21: visual
19: work
19: new
19: differ
18: practic
18: develop
18: data
16: also
```