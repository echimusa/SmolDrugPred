# Small Molecule Target Predicition
# This is ongoing collaborative project 
SmolDrugPred is ongoing (under development) AI and Machine Learning model to predict the binding behavior of small molecule drugs in Python. 
SmolDrugPred is an integrative computational framework to predict off-target interactions and potential associated antibiotic resistance in H. pylori for small molecules. 

Currently it uses FP6 fingerprints, and feeds them into a random forest classifier with a configurable number of trees. The sklearn random forest classifier holds all the decision trees in memory at the same time, and with the size of this data set (~200MB for just the features to SMILES with ChEMBL 25) the memory requirements increase rapidly along with the trees. It takes an AWS r5.4xlarge (with 128GB RAM) to train the model with 150 trees in the forest, and it would require roughly double the memory to serialize the model and save it for later use. Refactoring to a different random forest library, or writing our own, would help here.

Currently the model with only FP6 fingerprints for features and only 150 trees in the random forest achieves 78% for top-1 precision, recall, and F1 score. Although increasing the number of trees from 10 (77% accuracy) to 150 (78% accuracy) provides minimal improvement, it provides a measurable difference in top-5 accuracy. Top-5 accuracy increases in a linear fashion from 89% at 10 trees to 96% with 150. Adding more features from molecular descriptors or using an ensemble model would likely boost accuracy without much engineering effort. Also, experiments with different models such as Logistic Regression (like SwissTargetPrediction), SVMs, and neural networks should be tried, experiments are ongoing in the notebooks folder.

# UNDER CONSTRUCTION AND DEVELOPMENT #    
