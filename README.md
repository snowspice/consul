# consul
window10 +docker +consul 单机版作为配置中心
# 步骤
## 1. 安装 docker toolbox 【注意启动时，会虚拟化本地IP,本机为： 192.168.99.100】
    启动后，出现docker is configured to use the default machine with IP 192.168.99.100
    For help getting started, check out the docs at https://docs.docker.com
## 2. docker 启动consul
### 2.1  获取consul镜像
      docker pull consul
### 2.2 启动 consul
      docker run -d  -e CONSUL_UI_BETA=true --restart always -p 8500:8500 -p 8300:8300 -p 8600:8600 consul agent -server -bootstrap-expect=1  -bind=127.0.0.1 -client=0.0.0.0 -ui
### 2.3 验证启动是否成功
    
### 2.3.1  访问： 192.168.99.100:8500 
    如果UI界面出现，则启动成功
### 2.3.2  访问启动日志
     a)docker ps  查询出containerID
     b) docker logs $containerID   【实例：docker logs 0734eabe8ae2】
## 遇到的问题
  当启动完成后，我们通常会访问 http://localhost:8500 或者  http://127.0.0.1:8500 ,然后怎么也访问不到UI
  因为在本地docker初始化已经给分配了本地IP,那么访问一定要按照此IP 进行访问。
