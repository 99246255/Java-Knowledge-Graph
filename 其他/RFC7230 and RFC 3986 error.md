在tomcat 8.0.35之后 ,tomcat对url的参数做了比较规范的限制，必须按照RFC 7230 and RFC 3986规范，对于非保留字字符，如果不做转义处理，一律都会报The valid characters are defined in RFC 7230 and RFC 3986 错误。

解决这个问题的办法有几个：

    把非保留字字符做转义
    就是使用保留字字符
    要么就是换比较底一点的tomcat版本
    将json数据进行urlencode编码就可以了 即把json中的{}编码
