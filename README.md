# Digital Innovation One

Código criado para utilização junto a plataforma da Digital Innovation One

## Criação do cluster no Google Cloud Platform(GCP)

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


## Desafio GCP Dataproc

O desafio faz parte do curso na plataforma da Digital Innovation One:

__*Criando um ecossitema Hadoop totalmente gerenciado com Google Cloud Platform*__

O desafio consiste em efetuar um processamento de dados utilizando o produto Dataproc do GCP. Esse processamento irá efetuar a contahem das palavras de um livro e informar quantas vezes cada palavra aparece no mesmo.

---

### Etapas do Desafio

1. Criar um bucket no Cloud Storage
1. Atualizar o arquivo ```contador.py``` com o nome do Bucket criado nas linhas que contém ```{SEU_BUCKET}```.
1. Fazer o upload dos arquivos ```contador.py``` e ```livro.txt``` para o bucket criado (instruções abaixo)
    - https://cloud.google.com/storage/docs/uploading-objects

1. Utilizar o código em um cluster Dataproc, executando um Job do tipo PySpark chamando ```gs://{SEU_BUCKET}/contador.py```
1. O Job irá gerar uma pasta no bucket chamada ```resultado```. Dentro dessa pasta o arquivo ```part-00000``` irá conter a lista de palavras e quantas vezes ela é repetida em todo o livro.

