### 一、下载

搜索 es 7.10.0/Logstash 7.10.0/Kibana 7.10.0,跳转到elastic网站下载对应版本

### 二、安装方式

下载并解压即可

### 三、配置

1、ES配置：初步搭建，可不用配置

2、Logstash配置

在bin目录下创建logstash.conf文件，内容如下：

```java
input {
  tcp {
    port => 5044
  }
}

output {
  elasticsearch { hosts => ["localhost:9200"] }
  stdout { codec => rubydebug }
}
```

3、Kibana配置

启用如下配置：

```
server.port: 5601
server.host: "127.0.0.1"
elasticsearch.hosts: ["http://localhost:9200"]
```

### 四、启动

启动顺序：es--->logbash--->kibana

#### 1、启动es

直接进入bin目录，运行elasticsearch.bat文件

启动结果如下（我使用jdk8，所以启动会报错，但是并不影响服务的启动）：

![1605958599273](C:\Users\huayingcao2\AppData\Roaming\Typora\typora-user-images\1605958599273.png)

浏览器访问http://localhost:9200，结果如下：

![1605958801243](C:\Users\huayingcao2\AppData\Roaming\Typora\typora-user-images\1605958801243.png)

#### 2、启动logbash

进入bin目录，执行如下命令：

```
logstash.bat -f logstash.conf
```

启动过程如下：

![1605958732517](C:\Users\huayingcao2\AppData\Roaming\Typora\typora-user-images\1605958732517.png)

#### 3、启动kibana

进入bin目录，直接运行kibana.bat即可，运行结果如下：

![1605958861749](C:\Users\huayingcao2\AppData\Roaming\Typora\typora-user-images\1605958861749.png)

启动成功后在浏览器访问http://localhost:5601，如果启动成功，就会出现如下界面：

![1605958951220](C:\Users\huayingcao2\AppData\Roaming\Typora\typora-user-images\1605958951220.png)

至此，一个简单的KLE环境就搭建好了，更多更深更好玩的内容待我挖掘......