# Paper Link:
https://arxiv.org/ftp/arxiv/papers/1812/1812.08434.pdf
https://arxiv.org/pdf/2106.09135.pdf

# Graph Introduction
## Graphs
Basic conceptions

(1) are a kind of data structure which models a set of objects (nodes) and their relationships (edges).

(2) can be used as denotation of a large number of systems across various areas including social science (social networks、 protein-protein interaction networks.......)

(3) graph analysis focuses on tasks such as node classification, link prediction, and clustering.

## why Graph?

CNNs can only operate on regular Euclidean data like images (2D grids) and texts (1D sequences) while these data structures can be regarded as instances of graphs.

### Euclidean data (regular data)

![image](https://user-images.githubusercontent.com/94330800/146720538-0b1bb5c0-caed-403f-83ec-aea5ce770b28.png)

#### Non-euclidean data (irregular)

![image](https://user-images.githubusercontent.com/94330800/146720640-c73586b0-e3ce-4201-9409-029a6053db42.png)

### Euclidean data versus Non-euclidean data

![image](https://user-images.githubusercontent.com/94330800/146720883-2f8c1240-37a5-4a45-b3c1-ec6dc26490a8.png)


## Graph types

(1) Directed/Undirected Graphs.

![image](https://user-images.githubusercontent.com/94330800/147020736-5ac6f20b-d24d-4ad4-81af-8f9f28e2c401.png)

(2) Homogeneous/Heterogeneous Graphs（同构图、异构图）

nodes type + relation type >= 2

![image](https://user-images.githubusercontent.com/94330800/147020968-bf484dcf-2431-42c8-b9b6-7c687a51f6ac.png)

(3) Static/Dynamic Graphs

PyTorch： Dynamic -- Calculate while building
Tensorflow: Static --  Build first, calculate later

EEG graph is undirected,homogeneours graph

## Graph task

(1) Node-level
node classification, node regression, node clustering, etc.

(2) Edge-level
edge classification and link prediction (whether there is an edge existing between two given nodes.)

(3) Graph-level
graph classification, graph regression, and graph matching.

EEG Graph task is Graph-level classification

# EEG-Based GNN

## Current CNN-based EEG method

(1) Applying 2D convolutions to each EEG trial, which is presented by C×T, where C denotes number of EEG channels, and T denotes number of discretized time samples

(2) Applying 1D convolutions along only the time axis of the EEG trial, while treating the EEG channels as separate channels of the CNN processing (No sptial info).

## Graph Networks

(1) nodes:  each electrode used to collect EEG data according to intl. 10-5 system represents a node in the graph

(2) nodes' features: time samples acquired from an electrode corresponds to that node’s feature vector

(3) Adjacency matrix

i) every pair of nodes is connected by an unweighted edge 

ii) every pair of nodes is connected by an edge weighted by the functional neural connectivity factor, which is the Pearson correlation coefficient between the feature vectors of the two nodes

iii) a sparse adjacency matrix can be designed under the constraint only nodes that are closer than a heuristic distance are connected

## Advatanges 

One of the major drawbacks to using CNNs to classify EEG data is they fail to provide a brain connectivity mapping by identifying Regions of Interests (ROIs), whereas EEG-GNN can learn and visualize the connectivity between salient nodes, which addresses a critical issue of neuroscientific interpretability.
