# UDPServer

文件传输服务器

功能：
（1）监听请求，为每个Socket创建一个线程，动态维护当前已连接的Socket列表
（2）维护一个可获取文件列表，将文件绝对地址(rawFileName)映射到只含文件名的字符串(tinyFileName)，提供方法动态更新
（3）向Socket UDP传输请求的文件（若存在于文件列表）
（4）接收Socket传输的文件，存储到某个绝对地址，更新文件列表

对客户端：
首先发送helpDoc，
初始化Parser，
解析命令，执行相应操作
客户端输入特定命令(q)断开连接

命令：
list  请求可获取文件列表
get xx.xx  请求文件列表中的文件
//put xx.xx  通知服务器准备接收文件 
help  打印帮助文档
q  退出


客户端(初步)：
使用独立的一套内置命令
像服务器那样解析，执行完本地操作后对命令做相应调整，传输给服务器，如 put 在客户端要指定绝对路径，而在服务器只需指定自定义的文件名
