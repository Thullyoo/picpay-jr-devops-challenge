FROM python:3.9

WORKDIR /app

ADD ./requirements.txt ./requirements.txt

RUN pip install --no-cache-dir -r requirements.txt

ADD ./main.py ./main.py

EXPOSE 8081

CMD ["python", "main.py"]