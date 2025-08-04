# A first Tutorial 

## User guides

```
https://mit-submit.github.io/A2rchi/

```

## Set up your area

```
git clone https://github.com/mit-submit/A2rchi
cd A2rchi
pip install .

cp /home/submit/mariadlf/LLM_LPC_2005/A2rchi/configs/cms-ana-support.yaml configs
cp /home/submit/mariadlf/LLM_LPC_2005/A2rchi/configs/cms-ana.list  configs
cp /home/submit/mariadlf/LLM_LPC_2005/A2rchi/configs/prompts/cms-ana.prompt configs/prompts
cp -r /home/submit/mariadlf/.a2rchi-secrets ~/.a2rchi-secrets

export GRAFANA_PG_PASSWORD=XXXXXXX
a2rchi create --podman --gpu --name cms-ana-a2rchi --a2rchi-config configs/cms-ana-support.yaml --grafana True --document-uploader True
```

### check it's working


|             |              Command            |
| ----------- | ------------------------------- |
| open link   | http://submit76.mit.edu:50000   |
| grafana     | http://submit76.mit.edu:3001    |
| uploader    | http://submit76.mit.edu:5003/   |
| check image | podman image ls                 |
| check logs  | podman logs --follow chat-cms-ana-a2rchi |
| run image   | podman run -it --name cms-ana-a2rchi localhost/chat-cms-ana-a2rchi:2000 bash |


```
(myenvLLM) [mariadlf@submit76 A2rchi]$ docker ps -a
CONTAINER ID  IMAGE                                   COMMAND               CREATED         STATUS                   PORTS                     NAME
96639ffc8bb6  localhost/chromadb-cms-ana-a2rchi:2000  uvicorn chromadb....  49 minutes ago  Up 49 minutes (healthy)  0.0.0.0:8000->8000/tcp    chromadb-cms-ana-a2rchi
1454c7b67ae3  docker.io/library/postgres:16           postgres              48 minutes ago  Up 48 minutes (healthy)  5432/tcp                  postgres-cms-ana-a2rchi
5dde4ccf68b5  localhost/grafana-cms-ana-a2rchi:2000                         48 minutes ago  Up 48 minutes            0.0.0.0:3001->3000/tcp    grafana-cms-ana-a2rchi
cb784592ebe0  localhost/chat-cms-ana-a2rchi:2000      python -u a2rchi/...  48 minutes ago  Up 48 minutes            0.0.0.0:50000->50000/tcp  chat-cms-ana-a2rchi
6cad0614d4c3  localhost/uploader-cms-ana-a2rchi:2000  python -u a2rchi/...  48 minutes ago  Up 48 minutes            0.0.0.0:5003->5001/tcp    a2rchi-cms-ana-a2rchi_uploader_1
```
