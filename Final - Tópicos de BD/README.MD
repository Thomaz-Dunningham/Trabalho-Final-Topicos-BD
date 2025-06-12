# Desafio - Lab. final

## Roteiro

### Mudanças que precisaram ser feitas

#### 1 - Importar o csv do lab para o mongoDB
Usando o mongoDB, foi utilizado o mongoimport para inserir os dados do csv 'df_file' para dentro do mongoDB.

#### 2 - Atualizar as depências python para incluir o mongoDB e o ElasticSearch

#### 3 - Adaptar o docker compose dos containers para que eles todos pertençam a uma rede única e centralizada
Foi feita para que o Jupyter notebook pudesse integrar as dependências incluídas aos containers em execução.

## Comandos

### para baixar as dependências do mongo import
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
sudo apt-get update
sudo apt-get install -y mongodb-database-tools

### para importar o csv 
mongoimport mongodb://novo_user:senha123@localhost:27017/dbtopicosBD --type=csv --file="./Jupyter-notebook/notebooks/df_file.csv" --headerline

### para criar uma rede no docker
docker network create jupyter-mongo-net

## URLS -> ElasticSearch

### para listar os índices -> elastic
curl -X GET http://localhost:9200/_cat/indices?v

### para buscar pelo conteúdo dentro do index "csv_data"
curl -X GET "localhost:9200/csv_data*/_search?pretty"


## ETL -> 'csv_data'

### buscar pelo conteúdo do index
GET csv_data*/_search

### buscar com limite
GET csv_data*/_search
{
  "size": 5
}

## Consulta filtrando por campo
GET csv_data*/_search
{
  "query": {
    "match": {
      "Text": "election"
    }
  }
}

## subir docker-compose
docker compose --build -d