# Coding for the Digital Humanities: Pandas 

December 10th, 2024

- [Website link](https://dh-coding-docs.netlify.app/)
- [Home](README.md)

## Working with Databases

- Put the CSV into a table that allows you to filter and sort
- Remove empty columns
- Filter by english when using Omni
- Verify text encoding, as text contains errors such as the one below when opening with Excel:

```
Analysis of Scholar Collaboration Map Based on Graph Database Neo4j‚Äî‚ÄîTaking the Field of Digital Humanities as an Example

Neo4j--Taking --> Neo4j‚Äî‚ÄîTaking
```

This is an encoding issue with Excel, as the title appears as on the right when opening it with a text editor. Save the CSV with UTF-8 encoding. 

Chantal's process for cleaning data is to use Pandas and then open the CSV in [OpenRefine](https://openrefine.org/) in order to avoid issues with Excel like that above.

## Literature Review Example

The literature reivew CSV was generated using the following search terms:

- Any field contains: "digital humanities"
- Scope: Carleton + Omni Libraries / Carleton + Omni Libraries
- Start Date:  2004/01/01
- End Date:  2025/12/31
- Availability:  Peer-Reviewed Journals
- Resource Type:  Articles
- Langaue: English

However there were issues with non-English articles appearing in the search results, so I submitted a report to troubleshooting request to the Carleton library.

I downloaded 50 articles, filtered out the 10 articles with no abstract and then used the [langdetect](https://pypi.org/project/langdetect/) python package to filter out 11 non English articles. I then combined the remaining 29 articles into one string and tokenized it.

```
Full list of abstracts: 50
Filtered without NaN: 40
Filtered for English only: 29

Number of sentences: 179
Number of words: 6215
```

There is an issue with this character ```'“'``` not being caught by the stopwords filter after tokenization. It is different than this character ```'"'``` and does not get removed when I add it to the stopwords list using the extend method. 

```
Abstract frequency distribution:
95: humanities
90: digital
56: research
42: dh
26: analysis
25: field
24: topic
24: text
23: study
19: ”
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
```
```
Stemmed frequency distribution:
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
19: ”
19: work
19: new
19: differ
18: practic
18: develop
18: data
```

