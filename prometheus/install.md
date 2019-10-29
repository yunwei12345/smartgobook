

### 快速安装（docker版）



##### 1   下载镜像包

   ​               

```
ocker pull prom/node-exporter   #  该镜像用于主机系统数据的收集
docker pull prom/prometheus
docker pull grafana/grafana
```



##### 2   启动node-exporter



```
docker run -d -p 9100:9100 \
  -v "/proc:/host/proc:ro" \
  -v "/sys:/host/sys:ro" \
  -v "/:/rootfs:ro" \
    prom/node-exporter
```



##### 3   检查9100端口是否启动

​      

```
root@ubuntu:~# netstat -anpt
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1147/sshd       
tcp        0     36 192.168.91.53:22       192.168.91.1:63648      ESTABLISHED 2969/0          
tcp        0      0 192.168.91.53:22       192.168.91.1:63340      ESTABLISHED 1321/1          
tcp6       0      0 :::9100                 :::*                    LISTEN      3070/node_exporter

```



##### 4      访问 url     

```
http://192.168.150.53:9100/metrics   # 可以看到收集到的数据，有了它可以做数据展示
```

​                              ![](/images/b.png)







##### 5    启动prometheus



​     新建目录prometheus，编辑配置文件prometheus.yml

```
mkdir /opt/prometheus
cd /opt/prometheus/
vim prometheus.yml
```





```
global:
  scrape_interval:     60s          # 获取数据的时间间隔
  evaluation_interval: 60s          # 分析数据时间间隔

scrape_configs:
  - job_name: prometheus
    static_configs:
      - targets: ['localhost:9090']

  - job_name: linux
    static_configs:
      - targets: ['192.168.150.48:9100'] # 此处ip地址就是本机loacalhost
        labels:
          instance: linux

  - job_name: agent
    static_configs:
      - targets: ['192.168.150.53:9100']     # 远程被监控机器

```



启动 prometheus 



​         

```
docker run  -d \
  -p 9090:9090 \
  -v /opt/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml  \
  prom/prometheus
```



查看9090端口状态



  

```
root@ubuntu:/opt/prometheus# netstat -anpt
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1147/sshd       
tcp        0     36 192.168.91.132:22       192.168.91.1:63648      ESTABLISHED 2969/0          
tcp        0      0 192.168.91.132:22       192.168.91.1:63340      ESTABLISHED 1321/1          
tcp6       0      0 :::9100                 :::*                    LISTEN      3070/node_exporter
tcp6       0      0 :::22                   :::*                    LISTEN      1147/sshd       
tcp6       0      0 :::9090                 :::*                    LISTEN      3336/docker-proxy
```



访问url：

```
http://192.168.91.132:9090/graph
```





​           ![](images/a.png)



##### 6  启动grafana 



​          新建空文件夹grafana-storage，用来存储数据​  

​      

```
mkdir /opt/grafana-storage
```

​           

​        设置