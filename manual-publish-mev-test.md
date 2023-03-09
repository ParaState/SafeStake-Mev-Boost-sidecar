## manual publish mev (lighthouse bn+vc)

## 1 publish

---

Create local volume directory

```shell
# sudo docker stop safestake-mev-boost-sidecar-lighthouse-1 safestake-mev-boost-sidecar-geth-1 safestake-mev-boost-sidecar-mev-boost-1 safestake-mev-boost-sidecar-lighthouse-vc-1
# sudo docker rm safestake-mev-boost-sidecar-lighthouse-1 safestake-mev-boost-sidecar-geth-1 safestake-mev-boost-sidecar-mev-boost-1 safestake-mev-boost-sidecar-lighthouse-vc-1
# ll
sudo mkdir -p /data/jwt
sudo mkdir -p /data/geth
sudo mkdir -p /data/lighthouse
sudo mkdir -p /data/lighthouse-vc

```

Generate your jwt secret to jwt dirctory

```shell
# cat /data/jwt/jwtsecret
openssl rand -hex 32 | tr -d "\n" | sudo tee /data/jwt/jwtsecret
```

run

```shell
#cat docker-compose-operator-test.yml
#cat .env
sudo docker compose -f docker-compose-operator-test.yml up -d
#sudo docker logs -f safestake-mev-boost-sidecar-geth-1
#sudo docker logs -f safestake-mev-boost-sidecar-lighthouse-1
#sudo docker logs -f safestake-mev-boost-sidecar-mev-boost-1
#sudo docker logs -f safestake-mev-boost-sidecar-lighthouse-vc-1
```


---

## 2 Check

Check Geth (should show false)-交互终端下（`docker exec -it  xxx /bin/sh`）:
```shell
# sudo docker exec -it  safestake-mev-boost-sidecar-geth-1 /bin/sh
geth attach --datadir /data/geth --exec 'eth.syncing'
```

Check Lighthouse (should show {"data":"Synced"}):
```shell
curl localhost:5052/lighthouse/syncing
```

## 3 Begin Validating

```shell
# sudo docker exec -it safestake-mev-boost-sidecar-lighthouse-vc-1 /bin/sh
lighthouse account validator import --directory /data/lighthouse-vc/validator_keys
```