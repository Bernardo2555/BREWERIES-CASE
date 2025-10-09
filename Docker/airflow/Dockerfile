# FROM apache/airflow:2.7.1

# USER root

# # 🔧 Instala dependências do sistema
# RUN apt-get update && apt-get install -y \
#     wget \
#     openjdk-17-jdk \
#     procps \
#     curl \
#     python3-pip \
#     build-essential \
#     python3-dev \
#     && apt-get clean && rm -rf /var/lib/apt/lists/*

# # ⚙️ Configura variáveis de ambiente
# ENV JAVA_HOME="/usr/lib/jvm/java-17-openjdk-amd64"

# RUN mkdir -p /opt/airflow/logs && \
#     chown -R 50000:0 /opt/airflow/logs 

# RUN mkdir -p /opt/spark/events && \
#     chown -R 50000:0 /opt/spark/events
 


# # 🐍 Troca para o usuário airflow e instala pacotes Python
# USER airflow

# RUN pip install --upgrade pip

# RUN pip install --no-cache-dir \
#     apache-airflow-providers-apache-spark==4.0.0

FROM apache/airflow:2.7.1

USER root

RUN apt-get update && apt-get install -y \
    openjdk-17-jdk \
    curl \
    procps \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME="/usr/lib/jvm/java-17-openjdk-amd64"

RUN mkdir -p /opt/airflow/logs && chown -R 50000:0 /opt/airflow/logs

USER airflow
RUN pip install --no-cache-dir apache-airflow-providers-apache-spark==4.0.0