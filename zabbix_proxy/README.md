Role Name
======================
用于在目标节点主机安装zabbix_proxy，需提前安装好数据库

Requirements
=======================

ansible-mysql所需依赖
- MySQL-python


### 注意：
#### 1：
 当zabbix_proxy数据库为远程节点时，需要确定root远程账户Grant_priv是否开启，如下需要手动开启
 +-------------+---------------+------------+------------+
| host        | user          | Grant_priv | Super_priv |
+-------------+---------------+------------+------------+
| localhost   | root          | Y          | Y          |
| %           | root          | N          | Y          |
+-------------+---------------+------------+------------+
建议手动修改完成zabbix_proxy安装后还原

> use mysql;
> update mysql.user set Grant_priv="Y", Super_priv='Y' WHERE User='root';
> select host,user,Grant_priv,Super_priv from mysql.user where user='root';
+-----------+------+------------+------------+
| host      | user | Grant_priv | Super_priv |
+-----------+------+------------+------------+
| localhost | root | Y          | Y          |
| %         | root | Y          | Y          |
+-----------+------+------------+------------+

#### 2：
1）: 当zabbix_proxy为多节点 单个数据库地址不同库名时，host文件应如下配置，并注释var.yml相关变量
```
[all:vars]
ansible_ssh_pass
[proxy_host]
ansible_ssh_host=1.1.1.1 
DB_NAME=zabbix_proxy1 
HOSTNAME=zabbix_proxy1 
AGENT_SERVER=1.1.1.1 
```
2）：当proxy为多节点且每个proxy独立拥有数据库时，hosts文件应做如下配置，并注释var.yml相关变量
```
[all:vars]
ansible_ssh_pass
[proxy_host]
ansible_ssh_host=1.1.1.1 
DB_NAME=zabbix_proxy1 
HOSTNAME=zabbix_proxy1 
AGENT_SERVER=1.1.1.1
DB_ROOT=root 
DB_ROOTPASS=Asp@aspire+888 
DB_PORT=3306  
DB_HOST=10.12.70.42
```
