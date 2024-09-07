### Oracle新建用户

1. **创建用户名UAT 密码UAT**

   ```sql
   create user UAT identified by UAT
   ```

2. **创建表空间UAT 存放在D:\data\oracle 表空间大小100M**  

   ```sql
   create tablespace UAT datafile 'D:\data\oracle'
           size 100m
           autoextend on next 32m maxsize 2048m
   ```

3. **将名字为UAT的空间分配给UAT用户**

   ```sql
   alter user UAT default tablespace UAT
   ```

4. **给UAT用户授权**

   ```sql
   grant create session,create table,unlimited tablespace to UAT
   ```

   ```sql
   -- 给用户dba权限
   grant connect,resource,dba to UAT
   ```



### Oracle新建用户（docker版）

1. 进入镜像进行配置

   ```shell
   docker exec -it 容器名 bash
   ```

2. 在/home/oracle下创建tablespace文件夹

   ```shell
   mkdir /home/oracle/tablespace
   ```

3. 开启sql命令行

   ```shell
   sqlplus /nolog
   ```

4. 连接到数据库

   ```shell
   conn /as sysdba
   ```

5. 先创建新的临时表空间TEST_TEMP

   ```sql
   CREATE temporary TABLESPACE TS_FASM_TEMP tempfile '/home/oracle/tablespace/WMP_TEMP.DBF' SIZE 1024M AUTOEXTEND ON NEXT 32M;
   ```
   
   
   
6. 创建表空间TEST

   ```sql
   CREATE TABLESPACE TS_FASM LOGGING DATAFILE '/home/oracle/tablespace/TEST.DBF' SIZE 32M AUTOEXTEND ON NEXT 32M;
   ```
   
7. 创建用户UAT，密码是UAT

   ```sql
   CREATE USER UAT IDENTIFIED BY UAT
       ACCOUNT UNLOCK
       DEFAULT TABLESPACE TEST
       TEMPORARY TABLESPACE TEST_TEMP;
   ```

   > 修改用户
   >
   > ```sql
   > ALERT 
   > ```
   >
   > 

8. 赋予用户权限

   ```sql
   GRANT CONNECT,RESOURCE TO UAT;
   
   # 可选，DBA为数据库管理员权限
   GRANT DBA TO UAT;
   ```

9. 使用连接工具进行连接测试

**注意：exit可退出软连接**

 


### Oracle锁表

1. **查出被锁表**

   ```sql
   select object_name, machine, s.sid, s.serial# from v$locked_object l, dba_objects o, v$session s where l.object_id = o.object_id and l.session_id = s.sid;
   ```

2. **解锁进程（1172：sid）(15711：serial#)**

   ```sql
   alter system kill session '1172,15711'
   ```

   