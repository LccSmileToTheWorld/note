# 常用方法
 * start()：动当前线程；调用当前线程的run()
 * run()：常需要重写Thread类中的此方法，将创建的线程要执行的操作声明在此方法中
 * currentThread()：静态方法，返回执行当前代码的线程
 * getName()：获取当前线程的名字
 * setName()：设置当前线程的名字
 * yield()：放弃当前cpu的执行权
 * join()：线程a中调用线程b的join(),此时线程a就进入阻塞状态，直到线程b完全执行完以后，线程a才结束阻塞状态。
 * sleep(long millitime)：让当前线程“睡眠”指定的millitime毫秒。在指定的millitime毫秒时间内，当前塞状态。
 * isAlive()：判断当前线程是否存活
 * stop()：已过时。当执行此方法时，强制结束当前线程。
# 线程的优先级
* MAX_PRIORITY：10
* MIN _PRIORITY：1
* NORM_PRIORITY：5  -->默认优先级

如何获取和设置当前线程的优先级：
getPriority()：获取线程的优先级
setPriority(int p)：设置线程的优先级

说明：高优先级的线程要抢占低优先级线程cpu的执行权。但是只是从概率上讲，高优先级的线程高概率的情况下被执行，并不意味着只有当高优先级的线程执行完以后，低优先级的线程才执行。