# Graph Neural Networks for Particle Momentum Estimation in the CMS Trigger System


## Previous works

Shravan Chaudhari 


 -> Boosted Top dataset was used which was also used in the paper https://arxiv.org/abs/2104.14659

 
 -> https://github.com/Shra1-25/GSoC2021_BoostedTopJets/tree/main All the scripts are here

Emre Kurtoglu


 -> https://medium.com/@emre.kurt.96/gsoc-2021-graph-neural-networks-for-particle-momentum-estimation-in-the-cms-trigger-system-2216e4e4d005

## Overview of the project

In physics, momentum is a physical quantity describing a particle’s motion, calculated as the **product of its mass and velocity**. It is a fundamental quantity, essential for describing
the motion and interactions of objects and particles. A muon particle is a subatomic particle similar to an electron, but with a much greater mass (about 207 times heavier). It is a type of lepton that participates in electromagnetic and weak interactions, but not in strong nuclear forces.


The Compact Muon Solenoid (CMS) is a detector situated at the Large Hadron Collider (LHC) close to Geneva, Switzerland. This experiment identifies the particles produced from collisions and analyzes their kinematics through the coordinated effort of various sub-detectors.


High momentum muons are an important object in numerous physics analyses at Compact Muon Solenoid(CMS), making the precise calculation of muon momentum essential. As mentioned in the [paper](https://iopscience.iop.org/article/10.1088/1742-6596/1085/4/042042), accurately distinguishing high momentum (signal) muons from the overwhelming low momentum (background) muons is crucial for the efficiency of the EMTF trigger. This distinction significantly lowers background rates, enhancing the trigger's effectiveness in identifying events of interest.


A muon traveling through the endcap detectors has a chance to leave hits in four sequential stations labeled 1, 2, 3, and 4. The specific combination of hits is called the mode. For each detector we have **7 features, namely, Phi coordinate, Theta coordinate, Bending angle, Time info, Ring number, Front/rear hit and Mask**. In addition, we have 3 more road variables: pattern straightness, zone, median theta. Thus, in total we have 7x4+3 = 31 features for each event.


Using this information we have to estimate the momentum of the particle. Initially discretized boosted decision tree was used followed by Fully Connected Neural Networks (FCNNs) and Convolutional Neural Networks (CNNs). In this repo we try to explore more about the Graph Neural Networks(GNN) to estimate the momentum of the muon particles.

## Datasets

The dataset consists of 1179356 muon events generated using Pythia and could be downloaded from the following [link](https://www.kaggle.com/datasets/ekurtoglu/cms-dataset)


## [Graph Dataset Creation](https://github.com/Vishak-Bhat30/GSoC_24_GNN_For_Momentum/blob/main/Graph_creation)

- [x] **Each station as a node :** 
- [ ] **Each feature as a node :**
- [ ] **Each patch as a node :**

### 1. [Each station as a node](https://github.com/Vishak-Bhat30/GSoC_24_GNN_For_Momentum/blob/main/Graph_creation/Converting_to_graphs_eachstation_node.ipynb):
![APPROACH2png](https://github.com/Vishak-Bhat30/GSoC_24_GNN_For_Momentum/assets/102585626/ae9ea64e-a429-4a0e-a1b1-518868fc0558)

**Here basically each station(4),is made a node of the graph and the node feature is the features recieved at the respective station(7)**
    
    Here,
         Total nodes = 4
         node feature length = 7
         edges should be between these 4 nodes (Yet to find out the best way to decide across which two nodes there should be and edge)


### 2. [Each feature as a node](https://github.com/Vishak-Bhat30/GSoC_24_GNN_For_Momentum/blob/main/Graph_creation/Converting_to_graphs_eachfeature_node.ipynb):
![APPROACH1](https://github.com/Vishak-Bhat30/GSoC_24_GNN_For_Momentum/assets/102585626/1f295249-6a9f-4e28-9b2e-0ddb6d6a7e0e)


**Here basically each feature obtianed from different stations, here 4 stations are made a node of the graph and the node feature is the values of this feature across the 4 different stations**

    Here,
       Total nodes = 7
       node feature length = 4
       edges should be between these 7 nodes (Yet to find out the best way to decide across which two nodes there should be and edge)

