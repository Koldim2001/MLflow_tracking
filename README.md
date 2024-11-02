# Запуск mlflow + postgres + minio

## Установка переменных окружения

Создайте файлик `.env`, в который добавьте примерно следующее:

```bash
PG_USER=mlflow
PG_PASSWORD=mlflow
PG_DATABASE=mlflow
MLFLOW_BUCKET_NAME=mlfow-bucket
MINIO_ROOT_USER=admin
MINIO_ROOT_PASSWORD=admin1234
MLFLOW_S3_ENDPOINT_URL=http://localhost:9000
MLFLOW_TRACKING_URL=http://localhost:5000
MLFLOW_AWS_ACCESS_KEY_ID=qwerTY12345
MLFLOW_AWS_SECRET_ACCESS_KEY=poIuytRewq0987654321qwerty
```

## Запуск сервисов

Выполните:

```bash
docker-compose up -d
```

Когда контейнеры стартанут, на: 

* `http://localhost:9001/` будет доступен GUI Minio (логин/пароль – переменные `MINIO_ROOT_USER`/`MINIO_ROOT_PASSWORD` в `.env`);
* на `http://localhost:5050/` будет доступен GUI MLFlow;




### Код репозитория:

 > Результаты представлены в формате jupiter notebook: 
 > 1) Работа с PyTorch - [test_mlflow_pytorch.ipynb](https://nbviewer.org/github/Koldim2001/MLflow_tracking/blob/main/test_mlflow_pytorch.ipynb)
 > 2) Работа с Sklearn - [test_mlflow_sklearn.ipynb](https://nbviewer.org/github/Koldim2001/MLflow_tracking/blob/main/test_mlflow_sklearn.ipynb)

