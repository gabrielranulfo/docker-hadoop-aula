## Criar pasta odin no docker do odin:
hdfs dfs -mkdir -p /odin/

## Enviar um arquivo para o HDFS no docker do thor:
echo "Eu só quis ser como você, pai." > /tmp/thor.txt
hdfs dfs -put /tmp/thor.txt /odin/

## Listar arquivos no HDFS no docker do loki:
hdfs dfs -ls /odin/

## Ler o arquivo do HDFS no docker do odin:
hdfs dfs -cat /odin/thor.txt

## Listar HDFS
http://localhost:9870/

## Listar Cluster Resource Manager
http://localhost:8088/cluster

## Listar ApplicationsHistory
http://localhost:8188/applicationhistory

## Baixar um arquivo maior que o bloco
1 - Abra a pasta /tmp/ em algum docker

---
## Teste uma das duas opções
---
2a - Baixe através do link:
curl -L -o transactions-fraud-datasets.zip\
  https://www.kaggle.com/api/v1/datasets/download/computingvictor/transactions-fraud-datasets

2b-Copie a pasta extraida para o docker : docker cp ~/Downloads/finance_dataset/ 9459f3ae9bf9:/tmp/
---
3 - Suba para o cluster: hdfs dfs -put /tmp/transactions-fraud-datasets.zip  /odin/
4 - Acesse o HDFS va no diretório e observe que ao clicar sobre o arquivo que foi feito o upload mais de um bloco foi utilizado


## Apaga tudo
docker-compose down --volumes --remove-orphans

## Criar as iamgens
docker-compose up -d
