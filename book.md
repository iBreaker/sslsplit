# 程序通用架构


## 结构
### h文件
1. 头文件需要添加#ifnef宏，防止被重复引用
2. 声明公共的结构体、变量、枚举
3. 声明公共函数
4. 声明本模块中的extern变量
5. 不要再头文件定义变量和函数
6. 结尾添加vim modeline，防止vim讲h文件识别成cpp类型，导致多余的警告

### c文件
1. 定义本模块extern类型变量
2. 原则上尽量不用全局变量
3. 尽量通过传指针的方式调用
2. new本模块ctx
3. free本模块ctx

## 文件目录

### main
1. 打印帮助信息函数
2. 统一的错误退出函数，退出前给出提示
3. main函数只负责简单的各模块函数的调用，不写过于复杂的实现，使程序看起来清晰明了。

### version
1. 相关的的全局变量
2. 打印版本信息函数

### log

## 重要函数
### getopt
[看云](http://www.kancloud.cn/wizardforcel/linux-c-api-ref/98621)

```cpp
 #include<unistd.h>
 int getopt(int argc, char * const argv[], const char * optstring);
```

## 技巧
### 长字符串换行
 
 ```cpp
 	fprintf(stderr,
"Usage: %s [options...] [proxyspecs...]\n"
"  -c pemfile  use CA cert (and key) from pemfile to sign forged certs\n"
"  -k pemfile  use CA key (and cert) from pemfile to sign forged certs\n"
"  -C pemfile  use CA chain from pemfile (intermediate and root CA certs)\n"
"  -K pemfile  use key from pemfile for leaf certs (default: generate)\n"
"  -t certdir  use cert+chain+key PEM files from certdir to target all sites\n"
"              matching the common names (non-matching: generate if CA)\n"
"  -w gendir   write leaf key and only generated certificates to gendir\n"
"  -W gendir   write leaf key and all certificates to gendir\n"
"  -O          deny all OCSP requests on all proxyspecs\n"
"  -P          passthrough SSL connections if they cannot be split because of\n"
"              client cert auth or no matching cert and no CA (default: drop)\n"
)
 ```

