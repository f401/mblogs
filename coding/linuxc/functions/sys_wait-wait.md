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
- `status` 传入一个整形指针，用于保存子进程退出时的状态。传入`NULL`为不保存。

## 返回值：   

成功，返回子进程的`pid`;
失败，返回`-1`

## 例子
```c
#include <stdio.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <unistd.h>

int main(int argc, char *argv[]) {
  int pid = fork();
  if (pid < 0) {
    fprintf(stderr, "Fork Error %d\n", pid);
    return pid;
  } else if (pid == 0) { // 子进程
    return EXIT_SUCCESS;
  } else { // 父进程
    int status;
    wait(&status);
    printf(status == EXIT_SUCCESS ? "subprocess exit successfully"
                                                : "subprocess exit error");
  }
  return 0;
}
```
