# Paper Link:
https://arxiv.org/ftp/arxiv/papers/1812/1812.08434.pdf

# Introduction
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
