# tcp

[原文链接](https://juejin.im/post/5e89be166fb9a03c320ba688#heading-4)

## tcp基本知识

**tcp头部**

![tcp_head](https://github.com/yinabameguru/note/blob/master/tcp/resources/tcp_head.png)

**udp头部**

![udp_head](https://github.com/yinabameguru/note/blob/master/tcp/resources/udp_head.png)



**什么是tcp**

tcp是**面向连接**的、**可靠**的、**基于字节流**的传输层协议

***面向连接***：tcp协议是一对一连接的

***可靠***：tcp保证饱问一定能够到达接收端

***基于字节流***：消息有序，没有大小限制



**官方定义**

>*Connections: The reliability and flow control mechanisms described above require that TCPs initialize and maintain certain status information for each data stream. The combination of this information, including sockets, sequence numbers, and window sizes, is called a connection.--RFC 793*



**如何唯一确定一个tcp连接**

通过**四元组：源地址、源端口、目标地址、目标端口**确定唯一连接。源地址、目标地址**32位**，位于**ip头部**，用于**确定主机**。源端口、目标端口**16位**，位于**tcp**头部，用于**确定进程**



**tcp和udp的区别**

***1.连接***

tcp是面向连接的传输层协议，传输数据前先要建立连接

udp不需要连接，即刻传输数据

***2. 服务对象***

tcp是一对一的两点服务，即一条连接只有两个端点

udp 支持一对一、一对多、多对多的交互通信

***3. 可靠性***

tcp是可靠交付数据的，数据可以无差错、不丢失、不重复、按需到达

udp是尽最大努力交付，不保证可靠交付数据

***4. 拥塞控制、流量控制***

tcp有拥塞控制和流量控制机制，保证数据传输的安全性

udp则没有，即使网络非常拥堵了，也不会影响 udp的发送速率

***5. 首部开销***

tcp 首部长度较长，会有一定的开销，首部在没有使用「选项」字段时是 `20` 个字节，**如果使用了「选项」字段则会变长的**

udp首部只有 8 个字节，并且是**固定不变**的，开销较小



## tcp连接建立

**三次握手**

![three_handshake](https://github.com/yinabameguru/note/blob/master/tcp/resources/three_handshake.png)

**三次握手的三个报文**

![three_handshake_1_head](https://github.com/yinabameguru/note/blob/master/tcp/resources/three_handshake_1_head.png)

![three_handshake_2_head](https://github.com/yinabameguru/note/blob/master/tcp/resources/three_handshake_2_head.png)

![three_handshake_3_head](https://github.com/yinabameguru/note/blob/master/tcp/resources/three_handshake_3_head.png)



tips：linux可以通过[**netstat**](https://www.runoob.com/linux/linux-comm-netstat.html)命令查看网络连接状态



**为什么是三次握手，不是两次、四次？？**

**避免历史连接**

>*The principle reason for the three-way handshake is to prevent old duplicate connection initiations from causing confusion.---RFC 793*

//todo example

**同步双方序列号**

由于客户端、服务端双方都需要维护序列号，所以需要：1.客户端->服务端（syn）+服务端->客户端(ack)，同步客户端序列号 2.服务端->客户端(syn)+客户端->服务端(ack)，同步服务端序列号。总计4次握手，其中1的ack与2的syn可以合并优化，所以最终为3次握手

**避免资源浪费**

如果只有「两次握手」，当客户端的 `SYN` 请求连接在网络中阻塞，客户端没有接收到 `ACK` 报文，就会重新发送 `SYN` ，由于没有第三次握手，服务器不清楚客户端是否收到了自己发送的建立连接的 `ACK` 确认信号，所以每收到一个 `SYN` 就只能先主动建立一个连接，如果客户端的 `SYN` 阻塞了，重复发送多次 `SYN` 报文，那么服务器在收到请求后就会**建立多个冗余的无效链接，造成不必要的资源浪费。**