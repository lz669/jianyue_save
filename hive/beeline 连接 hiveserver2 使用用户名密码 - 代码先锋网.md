> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.codeleading.com](https://www.codeleading.com/article/739250704/)

> beeline 连接 hiveserver2 使用用户名密码，代码先锋网，一个为软件开发程序员提供代码片段和技术文章聚合的网站。

beeline connect 有几种方式，见 hive-site.xml, 缺省为 NONE。

```
<property>
    <name>hive.server2.authentication</name>
    <value>NONE</value>
    <description>
      Expects one of [nosasl, none, ldap, kerberos, pam, custom].
      Client authentication types.
        NONE: no authentication check
        LDAP: LDAP/AD based authentication
        KERBEROS: Kerberos/GSSAPI authentication
        CUSTOM: Custom authentication provider
                (Use with property hive.server2.custom.authentication.class)
        PAM: Pluggable authentication module
        NOSASL:  Raw transport
    </description>
  </property>
```

此时连接方式为

```
lcc@lcc ~$ beeline
Beeline version 1.2.1.spark2 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10014/default
Connecting to jdbc:hive2://localhost:10014/default
Enter username for jdbc:hive2://localhost:10014/default:
Enter password for jdbc:hive2://localhost:10014/default:
。。。。
Connected to: Apache Hive (version 2.1.0)
Driver: Hive JDBC (version 1.2.1.spark2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10014/default> show databases;
+----------------+--+
| database_name  |
+----------------+--+
| default        |
| lccdb          |
+----------------+--+
```

设置相应用户名和密码

```
<property>
    <name>hive.server2.thrift.client.user</name>
    <value>data1</value>
    <description>Username to use against thrift client</description>
  </property>
  <property>
    <name>hive.server2.thrift.client.password</name>
    <value>123456</value>
    <description>Password to use against thrift client</description>
  </property>
```

可以使用密码连接

```
3: jdbc:hive2://cdh-server2:10000/default> !connect jdbc:hive2://cdh-server2:10000/default
Connecting to jdbc:hive2://cdh-server2:10000/default
Enter username for jdbc:hive2://cdh-server2:10000/default: data1
Enter password for jdbc:hive2://cdh-server2:10000/default: *****
Connected to: Apache Hive (version 1.1.0-cdh5.14.4)
Driver: Hive JDBC (version 1.1.0-cdh5.14.4)
Transaction isolation: TRANSACTION_REPEATABLE_READ
```

注意这里设置的用户要求对 inode="/tmp/hive" 有执行权限，否则会出现下列问题：

```
Connecting to jdbc:hive2://localhost:10000/default
Enter username for jdbc:hive2://localhost:10000/default: hive
Enter password for jdbc:hive2://localhost:10000/default: **
Error: Failed to open new session: java.lang.RuntimeException: org.apache.hadoop.security.AccessControlException: Permission denied: user=hive, access=EXECUTE, inode="/tmp/hive":root:supergroup:drwxrwx---
    at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.check(FSPermissionChecker.java:319)
    at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.checkTraverse(FSPermissionChecker.java:259)
    at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.checkPermission(FSPermissionChecker.java:205)
    at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.checkPermission(FSPermissionChecker.java:190)
    at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkPermission(FSDirectory.java:1698)
    at org.apache.hadoop.hdfs.server.namenode.FSDirStatAndListingOp.getFileInfo(FSDirStatAndListingOp.java:108)
    at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getFileInfo(FSNamesystem.java:3817)
    at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.getFileInfo(NameNodeRpcServer.java:1005)
    at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.getFileInfo(ClientNamenodeProtocolServerSideTranslatorPB.java:843)
```