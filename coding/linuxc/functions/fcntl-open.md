# open

## 函数原型
```c
#include <fcntl.h>
int open (const char *file, int flags, ...);
```
## 功能
打开一个名为`name`的文件，返回这个文件的文件描述符(**fd**)，失败返回 -1

打开的文件描述符需要用`close`函数关闭

## flags
 - `O_RDONLY` 只读打开
 - `O_WRONLY` 只写打开 
 - `O_RDWR`   可读可写打开<br>
 ------------------------------------
  __打开/创建文件时，至少得使用上述三个常量中的一个。以下常量是选用的:__

 - `O_APPEND` 每次写操作都写入文件的末尾
 - `O_CREAT` 如果指定文件不存在，则创建这个文件
 - `O_EXCL` 如果要创建的文件已存在，则返回-1，并且修改errno的值
 - `O_TRUNC` 如果文件存在，并且以只写/读写方式打开，则清空文件全部内容
 - `O_NOCTTY` 如果路径名指向终端设备，不要把这个设备用作控制终端
 - `O_NONBLOCK` 设置为非堵塞

第三个参数只在创建文件时才会有效(`flag`包含`O_CREAT`), 为umask值

## 例子

```c
#include <fcntl.h>
#include <unistd.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

int main(int argc, char *argv[])
{
	const static char* msg = "Open Write Close Test";

	int fd = open("test.txt", O_WRONLY | O_CREAT, 0600);

	if (fd == -1) {
		fprintf(stderr, "打开文件失败, errno: %d\n", errno);
		return -1;
	}

	write(fd, msg, strlen(msg));
	close(fd);

	return 0;
}

```
