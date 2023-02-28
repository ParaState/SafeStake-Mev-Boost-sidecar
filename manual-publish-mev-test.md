## manual publish mev (lighthouse bn+vc)

## 1 publish

---

Create local volume directory

```shell
sudo mkdir -p /data/jwt
sudo mkdir -p /data/geth
sudo mkdir -p /data/lighthouse
sudo mkdir -p /data/lighthouse-vc

```

Generate your jwt secret to jwt dirctory

```shell
openssl rand -hex 32 | tr -d "\n" | sudo tee /data/jwt/jwtsecret
```

run

```shell
sudo docker compose -f docker-compose-operator-test.yml up -d
```


---

## 2 Check

Check Geth (should show false):
```shell
geth attach --datadir /data/geth --exec 'eth.syncing'
```

Check Lighthouse (should show {"data":"Synced"}):
```shell
curl localhost:5052/lighthouse/syncing
```

## 3 Begin Validating

```shell
lighthouse account validator import --directory /root/validator_keys
```