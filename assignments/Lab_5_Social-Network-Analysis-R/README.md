# Social Network Analysis using R

## R Programming Laboratory

### Aim

To implement Social Network Analysis using R by representing entities as
nodes and relationships as edges, analyzing network characteristics,
identifying important/influential nodes, visualizing the network, and
interpreting the obtained results.

## Problem Statement

The objective is to study Social Network Analysis using R and implement
the network-analysis workflow demonstrated in the prescribed tutorial.

The analysis represents entities as nodes/vertices and relationships as
edges/links. The network is then analyzed to understand its structure,
identify important or influential nodes, generate visualizations, and
interpret the obtained results.

## Dataset

The analysis uses `networkdata.csv`, the dataset provided with the
prescribed Social Network Analysis with R tutorial.

Dataset source:
https://github.com/bkrai/R-files-from-YouTube

## Technologies Used

- R
- RStudio/Google Colab
- igraph
- ggplot2

## Network Analysis Performed

The following analyses were performed:

1. Dataset loading and preprocessing
2. Network construction
3. Node and edge analysis
4. Degree analysis
5. In-degree and out-degree
6. Degree histogram
7. Network visualization
8. Network diameter
9. Edge density
10. Reciprocity
11. Closeness centrality
12. Betweenness centrality
13. Edge betweenness
14. Hub scores
15. Authority scores
16. Community detection using edge betweenness
17. Community visualization

## Community Detection Result

The edge-betweenness community detection algorithm identified 26
communities with a modularity value of approximately 0.35.

The largest detected community contains 10 nodes.

## Execution

The complete implementation is available in:

`Social_Network_Analysis.ipynb`

The notebook can be opened and executed using Google Colab with an R runtime.

## Conclusion

The experiment successfully demonstrates Social Network Analysis using R.
The network was represented using nodes and edges and analyzed using
different network measures, centrality measures, hub and authority scores,
visualizations, and community detection.
