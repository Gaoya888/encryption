# encryption

RSA 非对称加密，公钥加密，私钥解密。RSA算法基于一个十分简单的数论事实：将两个大素数相乘十分容易，但那时想要对其乘积进行因式分解却极其困难，因此可以将乘     积公开作为加密密钥；RSA加解密速度慢，不适合大量数据文件加密
AES 对称加密，密钥最长只有256个bit，执行速度快，易于硬件实现。由于是对称加密，密钥需要在传输前通讯双方获知;
    运行时不需计算机有非常高的处理能力和大的内存 加密速度快
OpenSSL 众多的密码算法、公钥基础设施标准以及SSL协议，或许这些有趣的功能会让你产生实现所有这些算法和标准的想法。 OpenSSL就是由Eric A. Young和Tim J.       Hudson两位绝世大好人自1995年就开始编写的集合众多安全算法的算法集合。通过命令或者开发库，我们可以轻松实现标准的公开算法应用。


 RSA算法介绍
 
 一、使用OpenSSL来生成私钥和公钥
    检测系统是否安装了 openssl
    openssl version -a
 1.生成私钥
 
    openssl genrsa -out rsa_private_key.pem 1024
    
 2.接下来根据私钥生成公钥
 
    openssl rsa -in rsa_private_key.pem -out rsa_public_key.pem -pubout
    
 3.这时候的私钥还不能直接被使用，需要进行PKCS#8编码：
 
    openssl pkcs8 -topk8 -in rsa_private_key.pem -out pkcs8_rsa_private_key.pem -nocrypt
    
    pk: in 后面读取文件  out  输出文件 -nocrypt 无密码输出
   
   
   AES算法
