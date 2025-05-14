FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

RUN groupadd -r flaskuser && useradd -r -g flaskuser flaskuser

COPY . .

RUN chmod -R 755 /app

USER flaskuser

EXPOSE 5000

CMD ["python", "app.py"]