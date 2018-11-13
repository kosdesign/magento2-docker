# magento2-docker
Magento2 + Varnish + PHP7 + Redis + SSL (cluster ready)

## Step: 1 - prepair your machine
#### - Install docker ( Link: https://www.docker.com/get-started )
=> Goto Docker -> Preferences -> File Sharing<br>
1. Add your work path
2. Composer path

#### - Change command name 3 files
=> redis-cli.sh, varnishadm.sh, varnishncsa.sh<br>
=> Replace <folder_name> with work folder name in lowercase<br>
=> Ex. work path is /Users/mac/Works/Magento2 - folder name is magento2

## Step: 2 - follow link below
Prototype => https://github.com/fballiano/docker-magento2#magento2-varnish--php7--redis--ssl-cluster-ready-docker-compose-infrastructure

Starting <folder_name>_db_1          ... done<br>
Starting <folder_name>_cache_1       ... done<br>
Starting <folder_name>_clusterdata_1 ... done<br>
Starting <folder_name>_apache_1      ... done<br>
Creating <folder_name>_varnish_1     ... done<br>
Creating <folder_name>_ssl_1         ... done<br>
Creating <folder_name>_cron_1        ... done<br>

#### - Install magento with sudo => sudo docker-compose up -d

#### - Database Server Host => db

#### - Deploy static files
docker exec -it <folder_name>_apache_1 bash
<br>
php bin/magento dev:source-theme:deploy
<br>
php bin/magento setup:static-content:deploy -f
<br>

#### - Reindex command
php bin/magento indexer:reindex
