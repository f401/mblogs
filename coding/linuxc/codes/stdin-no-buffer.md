# Linux下实现输入不缓冲

```c
void set_stdin_no_blocking() {
  struct termios tios;
  int id = tcgetattr(0, &tios);
  if (id == -1)
    perror("tcgetattr");
  printf("tios.c_lflag = %d\n", tios.c_lflag);
  tios.c_lflag &= ~(ICANON);//关闭标准
  tcsetattr(0, TCSAFLUSH, &tios);
}
```
