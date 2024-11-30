Project Overview

This project aims to develop a robust machine learning model to predict bankruptcy status for companies. It involves preparing training data, clustering companies into subgroups, and building stacked models for accurate prediction.
3.1 Training Data Preparation

To improve model efficiency, the number of features is reduced from 95 to between 25 and 50. The steps to prepare the data are:

    Feature Reduction:
        Select or engineer features to meet the target range (25–50 features).
        Use domain knowledge, feature selection, and engineering methods.

    Ensure Non-Multicollinearity:
        Features in the new training set must not be multicollinear. Validate using methods like correlation matrices or variance inflation factors (VIF).

    Gaussian Distribution:
        Transform each feature to follow a Gaussian distribution (e.g., log transformation or normalization).

3.2 Company Characterization

Clustering techniques are used to group similar companies to understand their general characteristics. The steps include:

    Clustering:
        Use unsupervised learning techniques to cluster companies into kk-many subgroups.
        The value of kk is based on team size:
            Minimum k=team sizek=team size
            Maximum k=2×team sizek=2×team size
        The target feature (Bankruptcy) is excluded during clustering.

    Analysis and Reporting:
        Number of Companies: Report the number of companies in each subgroup.
        Bankruptcy Balance: Show the balance of bankrupted companies in each subgroup.
        Subgroup Characteristics:
            Identify unique or helpful characteristics for each cluster.
            Use visualization techniques (e.g., plots, charts) to present these characteristics.

    Cluster IDs:
        Save the cluster IDs for each company. These will be used in the next section.

3.3 Building Training Models

This section involves building models to predict subgroup assignments and bankruptcy status within subgroups.
Step 1: Predict Subgroup Assignment

    Model:
        Use any supervised learning algorithm to predict the cluster ID for a company.
        High prediction accuracy is required; overfitting is acceptable at this stage.
    Feature Importance:
        Identify and report the most influential features for subgroup prediction.

Step 2: Stacking Model for Bankruptcy Prediction

A two-level stacked model is built:
Base Models

    Use non-parametric base models (e.g., decision trees, random forests).
    At least three base models are required for each subgroup.
    All base models for a subgroup must use the same features (features can differ between subgroups).

Meta Models

    Combine the outputs of the base models in each subgroup to build meta-models.

Responsibilities and Reporting

    Each team member works on at least one subgroup.
    Report the following for each subgroup:
        Team member's name.
        Subgroup(s) worked on.
        Model accuracy and confusion matrix (see format below).

Reporting Table Format:
Team Member	Subgroup	Accuracy	Confusion Matrix
Member A	Group 1	92%	[[50, 5], [10, 35]]
Member B	Group 2	88%	[[45, 8], [15, 32]]
4. Generalization

Transform the test dataset using the same process from Section 3.1. Use the trained models to predict each company's bankruptcy status.

    Submission Format: The results should be saved in a file following the format below:

Index	Bankrupt?
1	0
2	1
...	...
1012	1
Notes

    Ensure all features and transformations are consistent between the training and test data.
    Submit the final predictions in the specified format for evaluation.
