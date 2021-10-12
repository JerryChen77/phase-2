# 一、MySQL全局配置

- my.ini

## 1、文件路径

- MySQL默认安装
  - C:\ProgramData\MySQL\MySQL Server 5.7\my.ini

- 自定义安装
  - 安装路径下\my.ini



2、修改配置文件

| 修改配置文件                                                 |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210607104458982.png" alt="image-20210607104458982" style="zoom:80%;" /> |
| <img src="pictures/image-20210607104742958.png" alt="image-20210607104742958" style="zoom:80%;" /> |
| <img src="pictures/image-20210607104832591.png" alt="image-20210607104832591" style="zoom:80%;" /> |

注意：==一定要重启mysql服务，才能生效==

- 管理员进入cmd
  - net stop mysql服务名
  - net start mysql服务名