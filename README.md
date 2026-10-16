# LEAP-CS_Project

The project consist of a synthetic electrical network, where each of its nodes represent the substations of the network. We start with one substation that has suffered of an interruption of its service, and we want to predict which of the other substations also experience an interruption over 24 hours.

Our central question is *Do direct connectivity and local cross-links add predictive information beyond load and equipment age?*, that is, although our dataset contains information about the load and equipement age of each of the substations, we want to see if adding the spatial structure of the network modifies the results of the prediction of a regression model, that classifies the substations between those that will experience an interruption and those who will not.

The notebook is divided in three parts: in part 1 we load and explore the dataset via some plots. In part 2, we construct the network and start to study and visualize it. Finally, in part 3, we compare the logistic regression without network properties versus a logistic regression with network information, and discuss the results.

## Part 1: Data

As stated previously, the data consists of a synthetic electrical network of substations. The data is separated in two different dataframes. Τhe first one includes information about each of the substations, including its age, load ratio, connections to other substations and if it will later interrupt or not, which will be used to compare the models. The second one includes information about the connections between the different substations.

When exploring the data of the first dataframe, we can observe that there is a clear overload on the affected substations, while the equipement age is more overlapped with the ones that do not fail, suggesting a weaker correlation.


## Part 2: Network

We build an undirected unweighted network via the information on the second dataframe, using only the connections between them. We calculare the degree and clustering coefficient of each of the nodes.

When visualizing the network, we can see the connections between each substation, or the simulated electric grid. We also plot the local clustering coefficient versus the degree of the nodes, and we observe that at a higher degree, the local clustering tends to aroud 0.33.

## Part 3: Regression model

Finally, we compare two logistic regression models: one that takes into account only the load ratio and equipement age of each substation (data in the first dataframe), and a second one that also includes the network properties (degree and local clustering). When comparing the metrics and confusion matrices of each model (the detail being available in the Notebook), we observe that the network properties show a clear improvement on the predictive capacities of the model, which might be expected as the spatial distribution of the substations has a direct relation with the possible overloads of each simulated substation.
