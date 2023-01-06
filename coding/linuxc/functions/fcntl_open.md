# open

## 函数原型
`c
#include <fcntl.h>
int open (const char *file, int flags, ...);
`
## 功能
打开一个名为`name`的文件，返回这个文件的文件描述符(**fd**)，失败返回 -1

需要用`close`函数关闭
## Flags
 - O_RDONLY 只读打开
 - O_WRONLY 只写打开 
 - O_RDWR 可读可写打开
