# wait

## 函数原型
```c
#include <sys/wait.h>
pid_t wait(int *stat_loc);
```
## 功能
使用 `fork` 创建子进程后，父子进程的执行的先后顺序是不定的。
`wait`会暂停当前进程的执行，直到有信号到来或者子进程结束。
就是***阻塞父进程，等待子进程。***
