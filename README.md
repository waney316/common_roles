## 常用ansible role 任务编排

- mysql安装（采用二进制包）
- mysql升级
- zabbix_proxy部署（已编译包）



#### zabbix_proxy安装

- 如果zabbix_proxy和mysql绑定安装, 即1.1.1.1(zabbix_proxy/mysql) 2.2.2.2(zabbix_proxy/mysql), group_vars/zabbix_proxy做配置即可
- 如果zabbix_proxy和mysql异地部署, 即1.1.1.1/2.2.2.2(zabbix_proxy) 2.2.2.2(mysql), 需在inventory/hosts中定义如下信息：
```
1.1.1.1 DB_NAME=zabbix_proxy1 HOSTNAME=zabbix_proxy1
2.2.2.2 DB_NAME=zabbix_proxy2 HOSTNAME=zabbix_proxy2
```