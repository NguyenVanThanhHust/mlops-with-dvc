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

Configgure password and admin
```
dvc remote modify --local s3-data-storage access_key_id your_minio_user_name
dvc remote modify --local s3-data-storage secret_access_key your_minio_user_password
```


## Reference

https://medium.com/thecyphy/mlflow-with-dvc-bd7979969ea5
https://rachidbenouini.medium.com/data-version-control-from-zero-to-one-fcea7a1c48b3