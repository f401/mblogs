# tgkill
## 函数原型
```c
#include <signal.h>           /* Definition of SIG* constants */
#include <sys/syscall.h>      /* Definition of SYS_* constants */
#include <unistd.h>

[[deprecated]] int syscall(SYS_tkill, pid_t tid, int sig);

#include <signal.h>

int tgkill(pid_t tgid, pid_t tid, int sig);
```
## 功能
`tgkill` 向指定线程组`tgid`(`pid`)中的线程`tid`发送信号`sig`.
** NOTE ** :`kill`只能向进程发送信号
## 返回值
返回`0`表示成功，`-1`表示失败，并会设置`errno`表示错误原因
