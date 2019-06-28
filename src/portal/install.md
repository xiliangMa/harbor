
# deploy wizard


> 在<harbor-offline-installer-v1.8.0> 目录下

### 1. install and start environment
./install.sh --with-chartmuseum


### 2. stop all containers of harbor
docker ps | grep goharbor |awk '{print $1}' | xargs docker stop -f 


### 3. remove harbor-portal(ui) image
docker images | grep 'goharbor/harbor-portal'|awk '{print $3}' | xargs docker rmi 


### 4. import harbor-portal-v1.8.0 image
docker load < ../harbor-portal-v1.8.0.tar

### 5. backup old harbor tar
mv harbor.v1.8.0.tar.gz harbor.v1.8.0.tar.gz.bak


### 6. restart harbor
./install.sh --with-chartmuseum

