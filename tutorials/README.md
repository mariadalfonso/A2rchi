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

export GRAFANA_PG_PASSWORD=XXXXXXX
a2rchi create --podman --gpu --name cms-ana-a2rchi --a2rchi-config configs/cms-ana-support.yaml --grafana True
```

### check it's working


|             |              Command            |
| ----------- | ------------------------------- |
| open link   | http://submit76.mit.edu:50000   |
| check image | podman image ls                 |
| check logs  | podman logs chat-cms-ana-a2rchi |
| grafana     | http://submit76.mit.edu:3000   |



```
(myenvLLM) [mariadlf@submit76 A2rchi]$ podman image ls
REPOSITORY                            TAG                          IMAGE ID      CREATED         SIZE
localhost/chat-cms-ana-a2rchi         2000                         1b8992ebfbbd  4 minutes ago   30.9 GB
localhost/chromadb-cms-ana-a2rchi     2000                         745cf9622e37  16 minutes ago  749 MB
localhost/grafana-cms-ana-a2rchi      2000                         976e0d768901  17 minutes ago  423 MB
```
