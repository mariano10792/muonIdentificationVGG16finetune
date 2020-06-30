In this repository present, the scripts and notebooks were we develop muon identifier Convolutional Neural Network for CONNIE 1x5 experiment. 

Since all the runs are in root files we developed several extraction scripts:
- "extracRoot2Fits\masterCatalog.py" script generates the masterCatalog and apply some border cuts and bad events flagged.
- "extracRoot2Fits\GenImgFits.py" extracts individual fits and frame for each OHDU.

Then 4000 events were randomly sample:
- "humanClassification/Sample.ipynb" generates a sample of 200 runids from the masterCatalog.
- "humanClassification/GenerateAssets.py" generate informative images and histograms for human clasifiers random sampling 20 events from each runid.
- "humanClassification/GenerateAssetsTest.ipynb" can be used to test and improve this script.

Human-determined categorical labels were assigned to our train-test sample:
- "humanClassification/clasificador-New.ipynb" is the notebook used to label each event by the team.

- "humanClassification/InspectHumanLabels.ipynb" can be used to inspect the labels assined.

Then we apply data augmentation to balance our categories and make the model approximately invariant to random noise.
Next, the model after the training and validation process applied with KFold cross-validation.
- "fitModel/TrainModel.ipynb" 

We compute the classification results, the confusion matrix, and the performance of the model.

- "fitModel/InspectModels.ipynb"

Finally we apply our model to all events:
- "appyTimeSeries/runModel.py"
- "appyTimeSeries/TimeSeriesAnalysis.ipynb" helps to analyze the time series obtained by the model
