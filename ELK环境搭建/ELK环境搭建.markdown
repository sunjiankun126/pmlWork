### Docker下ELK的搭建

####1 准备镜像
使用elk集成镜像，地址：https://hub.docker.com/r/sebp/elk/tags

docker pull sebp/elk:660

####2 启动

	[root@centos-mq ~]# echo "vm.max_map_count=262144" > /etc/sysctl.conf
	[root@centos-mq ~]# sysctl -p // 将从指定的文件加载系统参数，如不指定即从/etc/sysctl.conf中加载
	[root@centos-mq ~]# docker run -dit --name elk \
    	-p 5601:5601 \
    	-p 9200:9200 \
    	-p 5044:5044 \
    	-v /opt/elk-data:/var/lib/elasticsearch \
    	-v /etc/localtime:/etc/localtime \
    	sebp/elk:660

说明：-p 指定映射端口，5601kibana访问，9200es端口，5044 logstash收集日志端口；-v 指定es数据目录

####3 访问

在浏览器中输入 http://172.171.15.79:5601/  172.171.15.79为部署的服务器的IP地址

####4 设置文件路径





