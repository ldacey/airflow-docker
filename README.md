# airflow-docker
Example docker-compose.yml file and entrypoint.sh script

Note that my Dockerfile is slightly edited currently to add the ADDITIONAL_PYTHON_DEPS argument which installs some required packages for me. 

My entrypoint.sh script is also edited a bit to create execute airflow upgradedb and to create an RBAC admin webserver user.

      docker build . \
      --build-arg PYTHON_BASE_IMAGE="python:3.7-slim-buster" \
      --build-arg PYTHON_MAJOR_MINOR_VERSION=3.7 \
      --build-arg AIRFLOW_INSTALL_SOURCES="apache-airflow" \
      --build-arg AIRFLOW_INSTALL_VERSION="==1.10.10" \
      --build-arg AIRFLOW_EXTRAS="async,aws,azure,celery,dask,jdbc,mysql,postgres,redis,slack,ssh,statsd,virtualenv" \
      --build-arg ADDITIONAL_PYTHON_DEPS="requirements.txt" \
      --build-arg CONSTRAINT_REQUIREMENTS="https://raw.githubusercontent.com/apache/airflow/1.10.10/requirements/requirements-python3.7.txt" \
      --build-arg ENTRYPOINT_FILE="entrypoint.sh" \
      --build-arg AIRFLOW_SOURCES_FROM="entrypoint.sh" \
      --build-arg AIRFLOW_SOURCES_TO="/entrypoint"
      --tag airflow:development
     
     
