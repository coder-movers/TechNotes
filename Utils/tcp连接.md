### windows测试tcp连接

- **使用 telnet:**

打开 cmd,输入:

```
telnet 127.0.0.1 8888
```

这会连接到 127.0.0.1 的 8888 端口。

>Windows 系统默认没有安装 telnet 客户端。
>
>可以通过以下步骤安装 telnet 客户端:
>
>1. 打开"控制面板"->"程序"->"启用或关闭Windows功能"
>
>2.勾选“Telnet 客户端”功能,点击确定。
>
>1. 等待安装完成,这需要一点时间。
>2. 之后打开 cmd,就可以使用 telnet 命令了。



- **使用测试 TCP 连接工具:**

1. 打开 PowerShell,输入:

```
Test-NetConnection 127.0.0.1 -Port 8888
```

2. 安装测试 TCP 连接模块:

```
Install-Module -Name PSTestConnection
```

3. 测试连接:

```
Test-TCP 127.0.0.1 -Port 8888
```



