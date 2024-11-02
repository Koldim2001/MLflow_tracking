# Использование MLflow для трекинга экспериментов PyTorch и Sklearn

MLflow - это инструмент для управления жизненным циклом машинного обучения, который предоставляет разработчикам и исследователям возможность отслеживать, управлять и развертывать модели машинного обучения. Одной из ключевых возможностей MLflow является трекинг экспериментов.  Он позволяет записывать параметры модели, метрики и артефакты (например, веса модели) во время обучения и сохранять их. Это позволяет легко сравнивать различные модели и эксперименты, а также повторять эксперименты с теми же параметрами.


MLflow поддерживает множество фреймворков машинного обучения, включая PyTorch и Sklearn. После завершения проведения экспериментов все записанные параметры, метрики и артефакты и сами модели будут сохранены (сохранить данные можно локально на компьютере или с использованием любой базы данных). Данные можно легко просмотреть с помощью удобного веб-интерфейса MLflow или использовать API для доступа.

## Запуск mlflow + postgres + minio


### Установка переменных окружения

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

### Запуск сервисов

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

Отдельно имеется файл test_s3.ipynb с примером того, как работать с MinIO. Для этого я сначала создал бакет test-bucket при запуске компоуза и теперь могу все что угодно в него класть и из него получать.
