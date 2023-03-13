# Flask API

Here is the Flask-API and how its deployed, you can use this document for further debugging.

### Files:

**app.py**

This code is no example for clean or secure code and should only be used for testing purposes and not in production.

```python
from flask import Flask, jsonify
import psycopg2
import os
import random

app = Flask(__name__)

conn = psycopg2.connect(
    host="postgresql",
    port="5432",
    database="postgres",
    user="postgres",
    password="URipXELhMA"
)

@app.route('/random-row')
def random_row():
    cur = conn.cursor()
    cur.execute('SELECT * FROM test ORDER BY RANDOM() LIMIT 1')
    row = cur.fetchone()
    cur.close()
    return jsonify(row)

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```



**requirements.txt**

```
Flask==2.1.2
psycopg2-binary==2.9.1
```



**Dockerfile**

```
FROM python:3.9-slim-buster

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```



### Deployment:

```
docker build -t your_flask_image:latest .
```

```
docker push your_dockerhub_username/your_flask_image:latest
```

