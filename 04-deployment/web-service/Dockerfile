FROM python:3.9.7-slim

RUN pip install -U pip
RUN pip install pipenv 

# The directpory where we want to copy the file 
WORKDIR /app

COPY [ "Pipfile", "Pipfile.lock", "./" ]

RUN pipenv install --system --deploy

COPY [ "predict.py", "lin_reg.bin", "./" ]

EXPOSE 9696

ENTRYPOINT [ "gunicorn", "--bind=0.0.0.0:9696", "predict:app" ]