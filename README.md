# mlops-with-dvc

## Install for the first time
Create virtual env
```
uv venv --python 3.12 && source .venv/bin/activate
```
Install package
```
uv sync
```

Start Data version control service
```
dvc init
```

On the minio address, for local is localhost:9001, login and create a bucket with name `dataset-v1`

Add storage bucket to dvc
```
dvc remote add -d s3-data-storage s3://dataset-v1/
```

Add storage endpoint
```
dvc remote modify s3-data-storage endpointurl http://localhost:9000
```

Configure password and admin
```
dvc remote modify --local s3-data-storage access_key_id your_minio_user_name
dvc remote modify --local s3-data-storage secret_access_key your_minio_user_password
```

Add your data folder
```
dvc add data/
```

Check status
```
dvc status
```
Push and pull data
```
dvc push
```
and 
```
dvc pull
```

## How to run
Pull latest data
```
dvc pull
```

Run main program
```
python main.py
```

Check result at
```
mlflow server --backend-store-uri mlruns/ --artifacts-destination mlruns/ --port 8000
```

## Reference

https://medium.com/thecyphy/mlflow-with-dvc-bd7979969ea5
https://rachidbenouini.medium.com/data-version-control-from-zero-to-one-fcea7a1c48b3