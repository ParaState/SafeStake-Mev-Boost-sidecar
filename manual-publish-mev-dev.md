manual publish to dev or test

---

vim .env 
```
cd /home/ubuntu/dvf/
# sudo vim .env.example
sudo vim .env

```

---

make  docker-compose-operator-mev.yml
```
sudo vim docker-compose-operator-mev.yml
```

---

run
```
sudo docker compose -f docker-compose-operator-mev.yml up -d
sudo docker ps
```