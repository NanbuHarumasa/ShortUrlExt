FROM python:3.10.7-slim


WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir --upgrade -r /app/requirements.txt
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y libopencv-dev

COPY main.py /app/

COPY logic/ /app/logic
COPY task/ /app/task

ENV GOOGLE_APPLICATION_CREDENTIALS /app/task/mws2022-cred.json

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8080"]