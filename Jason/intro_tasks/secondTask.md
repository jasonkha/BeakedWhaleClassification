# Summary of Kait Frasier's method

*Your second task is to read Kait Frasier's method and write a summary of it. Specifically, to differentiate two-phase automated clustering process.*

## Two-phase automated clustering process
The two-phased automated clustering process is used to group distinct click types into corresponding clusters. This problem was modeled as a weighted network in both phases, where the nodes represent different click types and the edges are the degree of pairwise similarity between the click types.

### Phase 1
The similarity metric $$S_{SPEC}$$ was calculated using correlation distance on the normalized spectral row vectors. Phase 1 clusters echolocation clicks from each 5-minute bin, with a parameter $$p_e$$ that controls the percentage of the weakest edges in the network to remove. When $$p_e$$ is set low enough ($$\leq$$ 90%), most of the nodes in the network were connected, as less than 0.2% of nodes were isolated. This meant on average, each bin had one cluster since many of the edges were still intact. When $$p_e$$ was increased to a very high pruning rate like 0.99, the mean clusters per bin increased such that 64.4% of the bins had more than one cluster. However, setting $$p_e$$ to 0.99 led to overfitting because only a small number of multi-cluster bins actually had more than one click type. Therefore, $$p_e$$ was set at 0.95 to provide a medium-level threshold to induce clusters with high and well-defined click similarity. For these clusters, statistics such as the mean spectral levels and modal ICIs became summary nodes and the input into Phase 2.

### Phase 2
In Phase 2, clustering was done on summarized results from Phase 1. For Phase 2, a combined similarity metric $$S_2$$ was used and it was defined as the product of $$S_{SPEC}$$ and $$S_{ICI}$$, the similarity metrics for the spectral and ICI information. ICI similarity was measured with the Euclidean distance between modal ICI values.

The Chinese whispers (CW) algorithm was used because it is fast for large networks and could identify clusters of any size, which is important when identifying rare click types.

If $$p_e$$$$\leq$$ 0.7, CW returned a single cluster with no isolated nodes. Also, mean normalized mutual information (NMI) was 1.0 because there were still enough edges to connect all the nodes. For larger values of $$p_e$$, NMI decreased initially, but then increased as $$p_e$$ approached 1. This was because the additional clusters became more specific and outlier values turned into isolated nodes. $$p_e$$ = 0.95 led to the most stable performance, identifying clusters with high mean NMI, without isolating too many nodes, partitioning clusters that are too small, or returning duplicate clusters.

Seven dominant click types (A-G) were identified in Phase 2 and they had consistent spectral shapes and modal ICIs.

The test nodes were classified by assigning each node to the click type with the highest similarity. Accuracy was determined by comparing the automated classification results with manual classifications done by analysts.
