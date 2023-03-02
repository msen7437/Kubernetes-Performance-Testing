# The Environment

### Description

1. #### Hardware

   - 3 Nodes (1 Master 2 Worker)

   - Each with 2 Cores and 8 GB RAM

   - Use any VM-Software you like

     

2. #### Cluster structure

   - We use k3s as our Kubernetes Engine, but any Kubernetes engine works fine

     

3. #### Running Applications

   - PostgreSQL Server filled with random data
   - Flask API that returns random data from the database when called
   -  [Monitoring components](Monitoring.md) 





### Building the environment:

- I assume you have your virtual machines or even physical nodes available
- Make sure that they can reach each other using ssh
- **The machines should all have different hostnames**



#### Installing k3s and connecting Nodes:

On the master:

```bash
curl -sfL https://get.k3s.io | sh -
```



For the worker nodes you need the token located in `/var/lib/rancher/k3s/server/node-token` in the master node and the address under wich the master node is reachable.



On both workers:

```bash
curl -sfL https://get.k3s.io | K3S_URL=https://myserver:6443 K3S_TOKEN=mynodetoken sh -
```

- Replace token and servername



**OR**

Follow these instructions: https://docs.k3s.io/quick-start



#### <u>!!OPTIONAL !!</u>

- Drain your master node to disallow scheduling on that node

  ```
  kubectl drain <nodeName>
  ```

  

#### Components and applications

**PostgreSQL:**

- For a Database Sever we will use bitnamis Postgres Helm-chart:

  - Create a file to store values:

    ```yaml
    ---
    volumePermissions:
      enabled: false
      securityContext:
        runAsUser: auto
    
    primary:
      extendedConfiguration: |
        password_encryption=md5
    
    auth:
      username: postgres
      password: postgres
      database: postgres
    ```

  - Install postgresql using the values:

    ```bash
    helm install postgresql --version=12.1.5 -f helm-bitnami-postgresql-values.yaml --repo https://charts.bitnami.com/bitnami postgresql
    ```



You need to create a table in your PostgreSQL Server:

```sql
CREATE TABLE test (data VARCHAR(255));
```



**Ingest random data in your database:**

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: postgres-random-data
spec:
  template:
    metadata:
      name: postgres-random-data
    spec:
      restartPolicy: Never
      containers:
      - name: postgres-client
        image: postgres:latest
        env:
        - name: PGPASSWORD
          value: URipXELhMA
        command:
        - bash
        - -c
        - |
          for i in {1..1000}; do
            random_data=$(openssl rand -base64 12)
            psql -h postgresql -U postgres -d postgres -c "INSERT INTO test (data) VALUES ('$random_data');"
          done
      imagePullSecrets:
      - name: my-registry-credentials
```

- You should checkout the logs to see if the ingestion worked properly



**Flask API:**

- I made a Docker Image for this specific usecase so no one has to write the Flask script themselves 

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: api-deployment
spec:
  selector:
    matchLabels:
      app: api
  replicas: 1
  template:
    metadata:
      labels:
        app: api
    spec:
      containers:
      - name: api
        image: zenseiii/flask-api:latest
        env:
        - name: DB_HOST
          value: postgresql
        - name: DB_PORT
          value: "5432"
        - name: DB_USER
          value: postgres
        - name: DB_PASSWORD
          value: postgres
        - name: DB_NAME
          value: test
        ports:
        - containerPort: 5000
```



**Exposing the API:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: api-service
spec:
  type: NodePort
  selector:
    app: api
  ports:
    - name: http
      port: 5000
      targetPort: 5000
```



Apply all the files using:

```bash
kubectl apply -f <filename>.yaml
```



If everything is up and running you should be able to access the API by just opening  `<NodeIP>:<ExposedPort>/random-row` in your Browser:

![image-20230301220039049](../Images/runningAPI.png)

In my case ii can only reach that API withing my network, wich is fine for our usecase.