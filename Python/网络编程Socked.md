#### 服务端

```python
# 服务端

import socket

server = socket.socket()
server.bind(("localhost", 8989))
server.listen(2)    #允许接收的连接数量

#result = server.accept()
#conn = result[0]
#address = result[1]
conn, address = server.accept() #accept方法返回的是二元元祖(链接对象,客户端地址信息)
#accept是阻塞连接,等待客户端链接,若没有链接,就卡在这一行不向下执行

print('客户端信息', address)
while True:
    #接受客服端信息,使用客户端和服务端的本次连接对象,而非server对象
    data = conn.recv(1024).decode('utf-8')#decode解码
    if data == "exit":
        break
    print(data)
    #recv接收的参数是缓存区大小,一般给1024
    #recv方法返回值是一个字节数组也就是bytes对象,不是字符串,通过decode方法utf-8解码将字节数组转换为字符串对象
    #发送回复消息
    msg = input().encode('utf-8')#encode放发通过utf-8编码
    conn.send(msg)
#关闭连接
conn.close()
server.close()
```





#### 客服端