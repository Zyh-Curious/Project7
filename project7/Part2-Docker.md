# Part2-Docker

1. **获取与部署**：拉取 mysql:8.0 镜像，以后台模式运行容器。将数据库 root 密码设为 123456，创建一个名为 user_db 的默认数据库，并将宿主机的 3306 端口映射出来供本地开发工具连接。
2. **数据持久化**：将 MySQL 容器内的数据目录（/var/lib/mysql）挂载到宿主机的 ~/mysql_data 目录，确保容器销毁后数据依然完好。

练习docker命令时已经拉取了mysql镜像（还有其他好玩的）：

![image-20261010131408378](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010131408378.png)





由于在上一个任务中安装的mysql被设置为开机自启且占用了3306端口，这里就映射了3307端口，其他操作一致，命令截图如下：

![image-20261010132154867](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010132154867.png



关闭虚拟机，在宿主机上安装mysql:

![image-20261010133710455](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010133710455.png)



访问成功：

![image-20261010134543971](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010134543971.png)



准备宿主机目录并授权：

![image-20261010135249687](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010135249687.png)



创建成功（不小心又拉了个8.0）：

![image-20261010135809094](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010135809094.png)



**3.连通验证与落库**：进入容器内部调用 mysql 命令行客户端，在 user_db 下创建一张 users 表并插入一条测试数据。



建表：

![image-20261010141821472](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010141821472.png)

插入数据：

![image-20261010142722567](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010142722567.png)



4**删除验证**：

![image-20261010143143420](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010143143420.png)

![image-20261010143320586](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261010143320586.png)





## 总结

通过实现数据持久化，能让数据更安全的保存在本机。同时分类掌握各个shell里的命令使用规范尤为重要（由于语法不规范，我重写了好几次T__T）

在整个任务过程中，我在mysql见表和插入数据时犯错较多，且多是因为没打“;”或没打引号

若是我出题，我会从镜像、容器、虚拟机三者的关系及具体操作等反面来进行考察；

本题的考察就挺全面的，出题人通过构建容器-虚拟机-宿主机的网络连接，全面考察了学者对各个shell命令的使用、对虚拟机网络架构的理解（不是拍马屁，只是我在做题过程中感受深刻）