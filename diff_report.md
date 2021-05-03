# Code Modification Report
Berikut adalah bagian-bagian kode yang diubah

## syscall.c
Line 109 - 112:
```C
#ifdef CS333_P1
// internally, the function prototype must be ’int’ not ’uint’ for sys_date()
extern int sys_date(void);
#endif // CS333_P1
```
Line 139 - 141:
```C
#ifdef CS333_P1
[SYS_date]    sys_date,
#endif
```

### syscall
Line 184 - 188:
```C
#ifdef CS333_P1
  #ifdef PRINT_SYSCALLS
    cprintf("%s->%d\n", syscallnames[num], num);
  #endif
#endif
```

## user.h
Line 47 - 49:
```C
#ifdef CS333_P1
int date(struct rtcdate*);
#endif // CS333_P1
```

## usys.s
Line 33:
```
SYSCALL(date)
```

## syscall.h
Line 24:
```C
#define SYS_date    SYS_halt+1
```

## sysproc.c
### sys_date
Line 109 - 110:
```C
cmostime(d);
return 0;
```

## proc.h
Line 52 - 54 (inside struc proc):
```C
#ifdef CS333_P1
  uint start_ticks;
#endif
```

## proc.c
### allocproc
Line 152 - 154:
```C
#ifdef CS333_P1
  p->start_ticks = ticks;
#endif
```

### procdumpP1
Line 570 - 574:
```C
uint elapsed = ticks-p->start_ticks;
uint elapsedLeft = (elapsed) / 1000;
uint elapsedRight = elapsed % 1000;

cprintf("\n%d\t%s\t%d.%d\t%s\t%d\t", p->pid, p->name, elapsedLeft, elapsedRight, states[p->state], p->sz);
```
