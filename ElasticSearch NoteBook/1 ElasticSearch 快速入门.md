# 安装

```shell script
# 安装 ElasticSearch
docker pull elasticsearch:7.2.0
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms512m -Xmx512m" -d --name es elasticsearch:7.2.0


docker exec -it es /bin/bash


# 修改跨域
vi /usr/share/elasticsearch/config/elasticsearch.yml

# 末尾加上
http.cors.enabled : true
http.cors.allow-origin : "*"


# 安装分词器
cd /usr/share/elasticsearch/plugins/
# 安装插件
elasticsearch-plugin install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.2.0/elasticsearch-analysis-ik-7.2.0.zip 
# 退出容器
exit
# 重启docker容器
docker restart es



# elasticsearch-head是用于Elasticsearch监控的插件
docker pull mobz/elasticsearch-head:5
docker run -d -p 9100:9100 docker.io/mobz/elasticsearch-head:5


# cat /proc/sys/vm/max_map_count
# 若max_map_count的值太小了，需要设大到262144
# sysctl -w vm.max_map_count=262144
vi /etc/sysctl.conf
# 文件最后添加一行: vm.max_map_count=262144

# 安装Kibanna
docker pull kibana:7.2.0

docker run -di --name kibana --link=es -p 5601:5601 kibana:7.2.0
# 将配置文件kibana.yml中的elasticsearch.url改为正确的链接，默认为: http://elasticsearch:9200，改为http://对应ip:
# 访问 http://ip:5601/