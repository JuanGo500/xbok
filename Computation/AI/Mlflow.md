# MLFlow

## Set up
In the code the tracking uri where output is logged must be set with `mlflow.set_tracking_uri("file:///content/drive/MyDrive/Data/mlruns")`
This saves to the mounted Google drive.

To retrieve data, open a Terminal    
`mlflow ui --backend-store-uri "file:///G:\Mi unidad\Data\mlruns"`