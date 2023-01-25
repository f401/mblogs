# wait

## 函数原型
```c
#include <sys/wait.h>
pid_t wait(int *stat);
```
## 功能
  使用 `fork` 创建子进程后，父子进程的执行的先后顺序是不定的。<br>
`wait`会暂停当前进程的执行，直到有信号到来或者子进程结束。<br>
就是***阻塞父进程，等待子进程。***  <br>  

  同时，如果子进程结束，会回收子进程;否则，子进程将转变为`僵尸进程`  <br>  

<br>
__NOTE__: 子进程结束信号: `SIGCHLD`

## 函数参数
- `status` 传入一个整形指针，用于保存子进程退出时的状态。`NULL`为不保存。

## 类似函数
[waitpid](sys_wait-wait.md)
