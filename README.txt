#Criação do cluster no Google Cloud Platform(GCP)

 - Criado uma conta free no GCP 
 - Ativar o serviço DataProc(digitar na barra de pesquisa do GCP 'Dataproc')
 - criar um cluster pelo Cloud Shell com os comandos abaixo:
  
  gcloud dataproc clusters create cluster-87a7 --enable-component-gateway \
  <n>--region us-central1 --zone us-central1-c \
  >--master-machine-type n1-standard-4 --master-boot-disk-size 500 \
  >--num-workers 3 --worker-machine-type n1-standard-2 \
  >--worker-boot-disk-size 500 --image-version 2.0-debian10 \
  >--optional-components JUPYTER,ZEPPELIN,ZOOKEEPER \
  >--expiration-time Tue Apr 19 2022 00:00:00 GMT-0300 (Horário Padrão de Brasília) \
  >--project projetoclouddio<n>

* com esses comandos o bucket foi criado automático

 ## Criando o job para estimar valor de PI pelo metodo monte carlo dentro do dataproc
    Classe Principal = org.apache.spark.examples.SparkPi
    Arquivos jar = file:///usr/lib/spark/examples/jars/spark-examples.jar
    argumentos = 1000
	linha de comando:
	gcloud dataproc jobs submit sparks \
        >--cluster="cluster-87a7" \
        >--region="us-central1" \
	>--class=org.apache.spark.examples.SparkPi \
	>--jars=file:///usr/lib/spark/examples/jars/spark-examples.jar \
	>-- 1000