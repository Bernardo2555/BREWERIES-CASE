# BREWERIES-CASE

I'm using Ubuntu 24.04.3

Tools:
    - Install Docker and docker compose
    - Python 3.12.3

Installing important arquives (same root as Dockerfile, spark only):
wget https://downloads.apache.org/spark/spark-4.0.1/spark-4.0.1-bin-hadoop3.tgz
tar -xvzf spark-4.0.1-bin-hadoop3.tgz
    
It was necessary to copy the files manually to opt/spark/jars (spark only):
commad (inside container)= docker cp ./Docker/spark-worker/spark-4.0.1-bin-hadoop3/jars/ spark-worker:/opt/spark/