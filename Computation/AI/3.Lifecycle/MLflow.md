# MLflow
Core Components:
When you run a machine learning script, MLflow Tracking records four main types of data:

- Parameters: Key-value inputs to your code (e.g., learning_rate=0.01, estimators=100).

- Metrics: Quantitative results used to evaluate the model (e.g., accuracy, RMSE, AUC). You can log these over time to create live progress charts.

- Artifacts: Files produced by the run. This includes the trained model files (e.g., a PyTorch .pth file or a Scikit-learn pickle), high-resolution plots, or CSV data samples.

- Metadata: Information about the environment, such as the specific Git commit used, the start/end time, and the user who ran the experiment.



## Set up
In the code the tracking uri where output is logged must be set with `mlflow.set_tracking_uri("file:///content/drive/MyDrive/Data/mlruns")`
This saves to the mounted Google drive.

To retrieve data, open a Terminal    
`mlflow ui --backend-store-uri "file:///G:\Mi unidad\Data\mlruns"`