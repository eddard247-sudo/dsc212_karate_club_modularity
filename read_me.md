# Modularity on the Karate Club Graph

**Course:** DSC-212

**Author:** Edward P Lamare

**Roll No:** IMS25075

## Overview

This project implements spectral modularity community detection from
(NumPy and NetworkX) on Zachary's Karate Club network with 34 members and 78 edges.
It splits the network recursively using the leading eigenvector of the
modularity matrix, draws the graph after every split, and tracks the four node
metrics: degree, betweenness, closeness and clustering.

## Acknowledgement of AI use

In line with the course instructor's encouragement to disclose AI use and my own lack of python skill, I used
Claude, Gemini, notebook and chatGPT as learning and coding assistants for this assignment.

**What the AI helped with**

- Walking me through the implementation in stages.
- Pointing out that NetworkX's built-in Karate Club graph carries edge weights,
  which has to be removed to get the 0/1 adjacency matrix the handout requires.
- Explaining why the code uses the corrected matrix M for sub-communities
  (Newman, 2006) and the extra positive-gain check.
- Suggesting ways to present results (pandas tables, which I didn't know how to implement) and reviewing my notebook
  against the handout's tasks.

I take responsibility for the submitted work. I have checked that I understand
the code and that the numbers in the discussion come from my own output.

## How to run

    pip install -r requirements.txt
    jupyter notebook DSC212_Karate_Modularity.ipynb

Then choose Kernel > Restart & Run All. The notebook runs from top to bottom
with no manual edits.

## Files

| File | Contents |
|---|---|
| `DSC212_Karate_Modularity.ipynb` | Code, outputs, plots and discussion |
| `requirements.txt` | Python packages needed |

## Results in brief

- Three splits give four communities of sizes: 7, 9, 12 and 6.
- afte each split, the modularity rises from 0 to 0.3715, 0.3727 and 0.3934.
- The first split divides the club into 16 and 18 members, contrary to thr real life 17-17 split. The odd one here is member 8.
- Nodes 0 and 33 which are, Mr. Hi and the club president, stay the most central nodes(The leaders) across the splits.

## Method note

For groups inside a larger partition, the code uses the corrected matrix
M = B(C) - diag(row sums of B(C)) from Newman (2006), instead of the raw
sub-block of B, and only accepts a split if its actual modularity gain is
positive. This is explaiend in the notebook.

## References

- Newman, M. E. J. (2006). Modularity and community structure in networks.
  *PNAS*, 103(23), 8577-8582.
- Zachary, W. W. (1977). An information flow model for conflict and fission
  in small groups. *Journal of Anthropological Research*, 33(4), 452-473.
