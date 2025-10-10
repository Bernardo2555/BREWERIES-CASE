# FROM openjdk:17-slim

# USER root

# # 🔧 Instala dependências básicas
# RUN apt-get update && apt-get install -y \
#     python3 \
#     python3-pip \
#     curl \
#     procps \
#     && apt-get clean && rm -rf /var/lib/apt/lists/*

# # ⚙️ Variáveis de ambiente
# ENV JAVA_HOME="/usr/local/openjdk-17"
# ENV SPARK_HOME="/opt/spark"
# ENV PATH="${JAVA_HOME}/bin:${SPARK_HOME}/bin:${SPARK_HOME}/sbin:${PATH}"

# # 🚀 Instala Apache Spark 4.0.1
# RUN mkdir -p ${SPARK_HOME} && \
#     curl -fSL https://downloads.apache.org/spark/spark-4.0.1/spark-4.0.1-bin-hadoop3.tgz -o /tmp/spark.tgz && \
#     tar -xzf /tmp/spark.tgz -C ${SPARK_HOME} --strip-components=1 && \
#     rm /tmp/spark.tgz

# # 🐍 Instala PySpark e Delta Lake
# RUN pip install --upgrade pip && pip install --no-cache-dir pyspark==4.0.1 delta-spark

# # 🔐 Ajusta permissões
# RUN chown -R 1000:1000 ${SPARK_HOME}
# USER 1000

FROM openjdk:17-slim

USER root

# Define variáveis
ENV SPARK_VERSION=4.0.1
ENV HADOOP_VERSION=3
ENV SPARK_HOME=/opt/spark
ENV PATH="$SPARK_HOME/bin:$SPARK_HOME/sbin:$PATH"

# Instala dependências
RUN apt-get update && apt-get install -y wget curl bash procps && \
    apt-get clean && rm -rf /var/lib/apt/lists/*


# Copia o Spark já extraído para o container
COPY spark-4.0.1-bin-hadoop3/ /opt/spark
COPY spark-defaults.conf /opt/spark/conf/spark-defaults.conf
RUN chmod -R 755 /opt/spark

# Inicia o Spark Master
CMD ["/opt/spark/sbin/start-master.sh"]