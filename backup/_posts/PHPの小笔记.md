---
title: PHPの小笔记
date: 2021-11-20 01:28:11
tags: 
- PHP 
- language
---
## 常量与变量
#### (PHP 是一门弱类型语言:
```php
<?php
$x_int=5;
$y_int=6;
$txt_string="Hello World!";
$float_num=4.0;
$z=$x+$y;
echo $z;
?>
```
#### PHP的数据类型：
`String（字符串 `` Integer（整型 `` Float（浮点型）``Boolean（布尔型）`
`Array（数组）``Object（对象）``NULL（空值）`
#### PHP的类型比较：

- 松散比较：使用两个等号 **==** 比较，只比较值，不比较类型。
- 严格比较：用三个等号 **===** 比较，除了比较值，也比较类型。
#### PHP的常量：
`bool define ( string $name , mixed $value [, bool $case_insensitive = false ] )`
Eg：`define("GREETING", "欢迎访问", true);`//true表示不区分大小写。
`$GREETING`和`$greeting`都会输出“欢迎访问”。
#### PHP 变量作用域：

- 全局变量除了**常规定义**，可以在函数内部使用`global`关键词来定义一个全局变量。
- php支持`static`关键词来定义静态局部变量。
#### PHP 超级全局变量
PHP中预定义了几个超级全局变量（superglobals） ，这意味着它们在一个脚本的全部作用域中都可用。 你不需要特别说明，就可以在函数及类中使用。
**PHP 超级全局变量列表:**
`$GLOBAL`   `$_SERVER`   `$_REQUEST`   `$_POST`
`$_GET`   `$_FILES`   `$_ENV`   `$_COOKIE`   `$_SESSION`
```php
//Example for $GLOBAL
<?php 
$x = 75; 
$y = 25;
function addition() 
{ 
    $GLOBALS['z'] = $GLOBALS['x'] + $GLOBALS['y']; 
}
addition(); 
echo $z; 
?>
```
`$_SERVER `是一个包含了诸如头**信息(header)**、**路径(path)**、以及**脚本位置(script locations)**等等信息的**数组**。这个数组中的项目由 Web 服务器创建。(不能保证每个服务器都提供全部项目)；(以下为表格：)

| $_SERVER['PHP_SELF'] | 当前执行脚本的文件名，与 document root 有关。例如，在地址为 http://example.com/test.php/foo.bar 的脚本中使用 $_SERVER['PHP_SELF'] 将得到 /test.php/foo.bar。__FILE__ 常量包含当前(例如包含)文件的完整路径和文件名。 从 PHP 4.3.0 版本开始，如果 PHP 以命令行模式运行，这个变量将包含脚本名。之前的版本该变量不可用。 |
| --- | --- |
| $_SERVER['GATEWAY_INTERFACE'] | 服务器使用的 CGI 规范的版本；例如，"CGI/1.1"。 |
| $_SERVER['SERVER_ADDR'] | 当前运行脚本所在的服务器的 IP 地址。 |
| $_SERVER['SERVER_NAME'] | 当前运行脚本所在的服务器的主机名。如果脚本运行于虚拟主机中，该名称是由那个虚拟主机所设置的值决定。(如: www.runoob.com) |
| $_SERVER['SERVER_SOFTWARE'] | 服务器标识字符串，在响应请求时的头信息中给出。 (如：Apache/2.2.24) |
| $_SERVER['SERVER_PROTOCOL'] | 请求页面时通信协议的名称和版本。例如，"HTTP/1.0"。 |
| $_SERVER['REQUEST_METHOD'] | 访问页面使用的请求方法；例如，"GET", "HEAD"，"POST"，"PUT"。 |
| $_SERVER['REQUEST_TIME'] | 请求开始时的时间戳。从 PHP 5.1.0 起可用。 (如：1377687496) |
| $_SERVER['QUERY_STRING'] | query string（查询字符串），如果有的话，通过它进行页面访问。 |
| $_SERVER['HTTP_ACCEPT'] | 当前请求头中 Accept: 项的内容，如果存在的话。 |
| $_SERVER['HTTP_ACCEPT_CHARSET'] | 当前请求头中 Accept-Charset: 项的内容，如果存在的话。例如："iso-8859-1,*,utf-8"。 |
| $_SERVER['HTTP_HOST'] | 当前请求头中 Host: 项的内容，如果存在的话。 |
| $_SERVER['HTTP_REFERER'] | 引导用户代理到当前页的前一页的地址（如果存在）。由 user agent 设置决定。并不是所有的用户代理都会设置该项，有的还提供了修改 HTTP_REFERER 的功能。简言之，该值并不可信。) |
| $_SERVER['HTTPS'] | 如果脚本是通过 HTTPS 协议被访问，则被设为一个非空的值。 |
| $_SERVER['REMOTE_ADDR'] | 浏览当前页面的用户的 IP 地址。 |
| $_SERVER['REMOTE_HOST'] | 浏览当前页面的用户的主机名。DNS 反向解析不依赖于用户的 REMOTE_ADDR。 |
| $_SERVER['REMOTE_PORT'] | 用户机器上连接到 Web 服务器所使用的端口号。 |
| $_SERVER['SCRIPT_FILENAME'] | 当前执行脚本的绝对路径。 |
| $_SERVER['SERVER_ADMIN'] | 该值指明了 Apache 服务器配置文件中的 SERVER_ADMIN 参数。如果脚本运行在一个虚拟主机上，则该值是那个虚拟主机的值。(如：someone@runoob.com) |
| $_SERVER['SERVER_PORT'] | Web 服务器使用的端口。默认值为 "80"。如果使用 SSL 安全连接，则这个值为用户设置的 HTTP 端口。 |
| $_SERVER['SERVER_SIGNATURE'] | 包含了服务器版本和虚拟主机名的字符串。 |
| $_SERVER['PATH_TRANSLATED'] | 当前脚本所在文件系统（非文档根目录）的基本路径。这是在服务器进行虚拟到真实路径的映像后的结果。 |
| $_SERVER['SCRIPT_NAME'] | 包含当前脚本的路径。这在页面需要指向自己时非常有用。__FILE__ 常量包含当前脚本(例如包含文件)的完整路径和文件名。 |
| $_SERVER['SCRIPT_URI'] | URI 用来指定要访问的页面。例如 "/index.html"。 |

#### PHP 魔术常量
| **__LINE__** | 文件中的当前行号。 |
| --- | --- |
| **__FILE__** | 文件的完整路径和文件名。如果用在被包含文件中，则返回被包含的文件名。
自 PHP 4.0.2 起，__FILE__ 总是包含一个绝对路径（如果是符号连接，则是解析后的绝对路径），而在此之前的版本有时会包含一个相对路径。
实例: |
| **__DIR__** | 文件所在的目录。如果用在被包括文件中，则返回被包括的文件所在的目录。
它等价于 dirname(__FILE__)。除非是根目录，否则目录中名不包括末尾的斜杠。（PHP 5.3.0中新增） |
| **__FUNCTION__** |  起本常量返回该函数被定义时的名字 |
| **__CLASS__** | 自 PHP 5 起本常量返回该类被定义时的名字（区分大小写）。 |
| **__TRAIT__** | ???? |
| **__METHOD__** | 返回该方法被定义时的名字（区分大小写）。PHP 5.0.0 新加 |
| **__NAMESPACE__** | 当前命名空间的名称（区分大小写）。此常量是在编译时定义的（PHP 5.3.0 新增）。 |

#### PHP 字符串变量
```php
<?php
$txt1="Hello world!";
$txt2="What a nice day!";
echo $txt1 . " " . $txt2;
?>
//Output:"Hello world! What a nice day!"
```
PHP同样有`strlen()`函数（
`strpos()`——查找字符
```php
<?php
echo strpos("Hello world!","world");
?>
//Output:"6"(7-1)
```
#### PHP 数组排序

- `**sort()**` - 对数组进行升序排列
- `**rsort()**` - 对数组进行降序排列
- `**asort()**` - 根据关联数组的值，对数组进行升序排列
- `**ksort()**` - 根据关联数组的键，对数组进行升序排列
- `**arsort() **`- 根据关联数组的值，对数组进行降序排列
- `**krsort() **`- 根据关联数组的键，对数组进行降序排列
#### PHP命名空间
#### PHP面向对象

---

