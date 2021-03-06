#### 1.java内存模型？

#####JMM

- java试图定义一种java内存模型来屏蔽各种硬件和操作系统层面的内存访问差异，以实现让java程序在各种平台上都能达到一致的访问效果。
- JMM的主要目标就是定义各个变量（不包括局部变量和方法参数，因为不存在竞争）的访问规则，即在虚拟机中将变量存储到内存中和从内存中取出变量这样的底层细节。
- 主内存和工作内存。

##### volatile

- 保证可见性，可见性是一个线程修改了变量的值，其他线程能立即知晓。（原理？）一定的有序性。不保证原子性。
- 使用限制:被写入volatile变量的值独立于程序的任何状态。
  - 对变量的写操作不依赖于当前值。
  - 该变量没有包含在具有其他变量的不变式中。
- 使用场景
  - 某些场景下volatile同步确实优于锁机制，但由于虚拟机对锁的消除和优化，很难量化比较。
  - 比起普通变量，volatile读性能几乎没差别，写性能差一些，因为要插入内存屏障指令。
  - 但大多数场景下，volatile性能还是优于锁，所以选不选volatile，主要看volatile语义能否满足场景。
  - 比如状态标志，一次性安全发布，定期“发布”观察结果，volatile bean模式，开销较低的“读-写锁”策略。
