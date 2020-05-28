### Role Name

mysql_install 

### Requirements

- net-tools
- unzip

### Role Variables

- MYSQL_VER：安装的mysql的版本号
- MYSQL_USER：mysql启动用户
- MYSQL_PORT：mysql监听端口
- MYSQL_PASSWD：mysql初始化root密码
- SOURCE_DIR：mysql安装包路径
- BASE_DIR：mysql安装基础目录
- DATA_DIR：mysql安装数据目录
- MYSQL_ID：IP后四位作为标识mysql的id

### Example Playbook

```yaml
- hosts: servers
  roles:
     # 运行mysql_install的role
     - mysql_install   
     # 运行mysql升级的role
     - mysql_upgrade
     
 # ansible-playbook role_name.yml
```

### Description

本role适用于centos7初次部署mysql，采用二进制安装

mysql安装信息配置：
    上述**Role Variables**均在vars/main.yml中定义，根据自行需要修改

mysql配置文件：

​	在template/my.cnf中配置






