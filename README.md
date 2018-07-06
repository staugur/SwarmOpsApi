# SwarmOps
Operation of swarm cluster, providing an intermediate layer application of API interface and UI.


## LICENSE
MIT


## Environment
> 1. Python Version: 2.7
> 2. Web Framework: Flask, Flask-RESTful
> 3. Required Modules: requirements.txt


## Usage

```
1. Requirement:
    1.0 yum install -y gcc gcc-c++ python-devel libffi-devel openssl-devel
    1.1 pip install -r requirements.txt
    
2. modify config.py or add environment variables(os.getenv key in the reference configuration item):
    """
    此处解释一个配置: GLOBAL段中的Authentication, 用来做认证的, 可选sso和none; 
    默认是sso, 会使用https://github.com/staugur/passport做认证，但是此已经更新，swarmops暂未适配，所以无法使用。
    当下，您可以自行做认证，如果不想认证, 改为none, 或者启动前设置环境变量: export swarmops_authentication=none
    """

3. run:
    3.1 python main.py        #开发模式
    3.2 sh Control.sh         #生产模式
    3.3 python -O Product.py  #生产模式，3.2中方式实际调用此脚本
    3.4 python super_debug.py #性能分析模式
```


## Usage for Docker

```
   cd misc ; docker build -f Dockerfile_gcc -t alpine:gcc .
   cd .. ;   docker build -t swarmops .
   # 设置无认证，默认sso，会使用passport(passport重构，此项目暂为适配)
   docker run -tdi --name swarmops --net=host -e swarmops_authentication=none swarmops
   ps aux|grep SwarmOps //watch the process
```


## UI
![Swarms][2]
![Services][3]
![Nodes][4]
![Storages][5]
![Network][7]
![Registry][8]


## Release Note

*For more info, please read the changelog.md*

####Release 0.0.1

*作为第一个正式发布版本，SwarmOps实现了对Docker Swarm模式的集群管理，所有操作均采用API形式。*

```
1. UI/API可以初始化、管理多个Swarm集群
2. UI/API可以增删查改服务
3. UI/API可以增删查改节点
4. UI/API可以查询服务的其他属性, 例如replicas节点，并生成Nginx样例配置
5. 数据持久化存储local或redis, 使用redis可以多点部署
6. 认证采用passport, 并设置只允许登陆的用户列表
```

####Release 0.0.2

```
1. UI大部分功能重磅更新, 采用layer弹层方式取消跳转
2. UI集成私有仓, 支持V1版本, 查删操作
3. network查询
```

####Release 0.0.3

```
```

## TODO

Not yet developed(暂不开发)


  [1]: ./misc/SwarmOpsApi.png
  [2]: ./misc/swarm.png "集群"
  [3]: ./misc/service.png "服务"
  [4]: ./misc/node.png "节点"
  [5]: ./misc/storage.png "存储"
  [7]: ./misc/network.png "网络"
  [8]: ./misc/registry.png "私有仓"
