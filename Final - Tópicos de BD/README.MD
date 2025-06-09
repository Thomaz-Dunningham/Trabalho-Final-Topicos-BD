# Desafio - Lab. final

### para baixar as dependências do mongo import
``` bash
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
sudo apt-get update
sudo apt-get install -y mongodb-database-tools
```

### para importar o csv
``` bash
mongoimport mongodb://novo_user:senha123@localhost:27017/dbtopicosBD --type=csv --file="./Jupyter-notebook/notebooks/df_file.csv" --headerline
```

## subir os docker-compose
``` bash
docker compose --build -d
```
