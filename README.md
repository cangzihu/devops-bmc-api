

1.基础环境介绍;

   软件版本信息  |系统/内核信息 |项目目录功能介绍
  -|-|-
  Python3.6     |Centos 7.2 | tools 数据库相关配置和ansible 动态主机
  Flask1.0.2    |3.10.0-862.6.3.el7.x86_64  |boot.py flask 程序启动入口文件
  Ansible2.7.7  |           | ansibleManage ansibleApi核心管理功能模块
  MYSQL5.6.0    |           |    


2.项目系统依赖包安装;
  (1).centos 7x系统安装支持包;  
  
   yum -y install python36 mysql-devel libxml2* mysql initscripts python36-devel python36-pip python36-setuptools mysql-devel libxml2*      mysql initscripts psmisc  
   
   
   (2).安装项目依赖包pip方式;  
   
   /usr/local/bin/pip3.6 install --upgrade pip  
   /usr/local/bin/pip3.6 install --upgrade setuptools  
   /usr/local/bin/pip3.6 install requests  
   /usr/local/bin/pip3.6 install Jinja2==2.10  
   /usr/local/bin/pip3.6 install flask-sqlalchemy  
   /usr/local/bin/pip3.6 install ansible  
   /usr/local/bin/pip3.6 install PyMySQL==0.9.3  
   /usr/local/bin/pip3.6 install gevent  
   /usr/local/bin/pip3.6/flask==1.0.2  
    /usr/local/bin/pip3.6/request==1.0.2  
    /usr/local/bin/pip3.6/Jinja2==2.10  
    /usr/local/bin/pip3.6/Flask-Cors==3.0.6  
    /usr/local/bin/pip3.6/flask-sqlalchemy  
    /usr/local/bin/pip3.6/flask_restful  
    /usr/local/bin/pip3.6/jsonify  
    /usr/local/bin/pip3.6/ansible  
    /usr/local/bin/pip3.6/MySQL-python    
    
3.接口文档介绍;  
(1).ansible动态主机接口;  

**devops-bmc-api 接口文档：** 

- 增加ansible 动态主机

**请求URL：** 
- ` http://devops-bmc-api.com/ansible/host/v1 `
  
**请求方式：**
- POST  

**格式：**  
- JSON  

**参数：** 

|参数   |必填   |类型   |说明   |
| ------------  | ------------ | ------------ | ------------ |
| instanceip    |是   |str   |执行端合法ip地址, 默认值:None,支持多个ip地址添加","隔开".
| username      |是   |str   |系统登录账号名称，参数ansible项目未使用
| password      |是   |str   |系统登录密码名称，参数ansible项目未使用
| port          |是   |str   |系统登录远程ssh端口，默认值22端口
| group         |是   |str   |系统机器分组，建议跟进环境维度进行分组(dev,test,ontest,prod)进行.


 **请求示例**
```
{
	 "instanceip":"192.168.77.111,192.168.77.112,192.168.76.111,192.168.79.112",
	 "username":"ops",
	 "password":"ops",
	 "port":"22",
	 "group":"test"
}
```
 **返回参数**
```
{
    "code": 0,
    "data": "Insert Success"
}
```

 **备注** 

- code状态码描述
  0 表示系统正常响应;
  1 表示系统内部出现问题;  
 
- 查询 ansible 动态主机列表

**请求URL：** 
- ` http://devops-bmc-api.com/ansible/host/v1 `
  
**请求方式：**
- GET  

**格式：**  
- JSON  
**请求参数**  
http://devops-bmc-api.com/ansible/host/v1  

 **返回参数**
```
{
"code": 0,
"total": 4,
"data": [
{
"id": 5,
"host": "192.168.77.111",
"username": "ops",
"password": "ops",
"port": "22",
"group": "testone"
},
{
"id": 7,
"host": "192.168.77.112",
"username": "ops",
"password": "ops",
"port": "22",
"group": "testone"
},
{
"id": 8,
"host": "192.168.76.111",
"username": "ops",
"password": "ops",
"port": "22",
"group": "testone"
},
{
"id": 9,
"host": "192.168.79.112",
"username": "ops",
"password": "ops",
"port": "22",
"group": "testone"
}
]
}
```

 **备注** 

- code状态码描述
  0 表示系统正常响应;
  1 表示系统内部出现问题;  
  
  
  
(2).ansible 执行接口;  




4.数据流走向图;
![项目数据流走向](https://github.com/breaklinux/devops-bmc-api/blob/master/img/devops-bmc-api.jpg)
    
