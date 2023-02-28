manual publish to dev or test

---

vim .env 
```
 sudo mkdir -p /data/geth
 sudo mkdir -p /data/lighthouse
 sudo mkdir -p /data/jwt
 sudo mkdir -p /data/operator

```





---

run
```
sudo docker compose -f docker-compose-operator-mev.yml up -d

```