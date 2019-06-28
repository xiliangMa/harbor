
### 安装以及切换定制版ui



在<harbor-offline-installer-v1.8.0> 目录下

##### 1 -------- install and start environment
./install.sh --with-chartmuseum


##### 2 -------  remove all containers of harbor
docker ps | grep goharbor |awk '{print $1}' | xargs docker rm -f 


##### 3 -------   remove harbor-portal(ui) image
docker images | grep 'goharbor/harbor-portal'|awk '{print $3}' | xargs docker rmi 


(更新并重新加载新的portal ui，从第4步开始)
##### 4--------   import harbor-portal-v1.8.0
docker load < ../harbor-portal-v1.8.0.tar

##### 5-------  rename harbor tar
mv harbor.v1.8.0.tar.gz harbor.v1.8.0.tar.gz.bak


##### 6-------  restart harbor
./install.sh --with-chartmuseum


*** 重新修改portal UI后，从第4步开始执行，使用新的UI
