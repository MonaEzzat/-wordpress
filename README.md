
#!/bin/bash
cd /wordpress/mysql
docker build -t doci/mysql .
cd /wordpress
docker build -t doci/downloader .
cd /wordpress/phpfpm/
docker build -t doci/phpfpm .
cd /wordpress/nginx
docker build -t doci/nginx .
docker run -d --name mysql doci/mysql
docker run -i -t --name downloader doci/downloader
docker run -d --name app1 --volumes-from downloader --link mysql:db doci/phpfpm

docker run -d --name app2 --volumes-from downloader --link mysql:db doci/phpfpm
docker run -d -p 8080:80 --name nginx --volumes-from downloader --link app1:app1 --link app2:app2 doci/nginx
#docker exec app1 cat /etc/hosts | grep db  //to show my sql db ip 
#docker exec app1 env
