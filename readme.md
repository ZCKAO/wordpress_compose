#wordpress

##VW Setup

```commandline
sudo apt update
sudo apt install -y docker docker-compose
```

```commandline
# 下載必要檔案
sudo docker-compose -f docker-compose.yml.http pull

# 執行網站
sudo docker-compose -f docker-compose.yml.http up -d
```

### SSL
```commandline
# 關閉之前的機器
sudo docker-compose -f docker-compose.yml.http down

# 調整設定檔案
# 將 `ubestream.cf` 改成自己的網域
vim docker-compose_certbot.yml

# 進行網域認證
sudo docker-compose -f docker-compose_certbot.yml up
```

```commandline
# 關閉網域認證用的機器
sudo docker-compose -f docker-compose_certbot.yml down

# 調整設定檔案
# 將 `ubestream.cf` 改成自己的網域
vim nginx-conf-https/nginx.conf 

# 以SSL方式開啟網站
sudo docker-compose -f docker-compose.yml.https up -d
```

## docker-compose debug
```commandline
# 查看紀錄檔案
sudo docker-compose -f <docker-conmpse filename> logs -f

# 改變檔案權限
sudo chmod -R 777 <path>
```