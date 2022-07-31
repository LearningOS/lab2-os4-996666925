## 总结
通过给TaskControlBlock添加开始时间和调用次数两个字段。在run_next_task的时候记录一下开始时间。并且在系统调用开始的时候记录次数。

## 简答作业

1.  
RustSBI version 0.2.2  
[ERROR] [kernel] PageFault in application, bad addr = 0x0, bad instruction = 0x80400408, core dumped.  
[ERROR] [kernel] IllegalInstruction in application, core dumped.  
[ERROR] [kernel] IllegalInstruction in application, core dumped.  

第一个是访问了非法地址，后两个是使用了非法指令。  
2.  
    1.a0代表返回值。使用场景：（1）刚开始时进入用户态。（2）中断之后返回用户态  
    2.sstatus:SPP等字段给出Trap发生之前CPU的特权机信息。  
      sepc:记录Trap发生之前执行的最后一条指令地址。  
      sscratch:内核栈位置  
    3.x2:已经保存了。x4:用不到  
    4.sp指向用户栈，sscratch指向内核栈。  
    5.sret指令。CPU 会将当前的特权级按照 sstatus 的 SPP 字段设置为 U 或者 S，然后跳转到 sepc 寄存器指向的那条指令，然后开始向下执行。  
    6.sp指向内核栈，sscratch指向用户栈。  
    7.ecall  

