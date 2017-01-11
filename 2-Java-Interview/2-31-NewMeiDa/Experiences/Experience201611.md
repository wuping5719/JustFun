<h3> 2016-11：美团点评(NewMeiDa)秋招 北京站(望京)</h3>
   美团点评校招最后一批做的的笔试题，一直没消息，以为挂了。没想到11月初，都快签了，收到了面试邀约。邮箱里还躺着Oracle的笔试邀约，心中五味杂陈。学校在岛城，去一趟帝都不容易啊，纠结中。
   
   收到美团邀约时已签其他公司，搜集的面经，根据面经看书，更有针对性。
   
* 1.把一颗二叉树同层的节点用next指针链接起来.     
  <http://www.cnblogs.com/shawnhue/p/leetcode_116_117.html>    
* 2.Spring Bean对象的生命周期.      
  Spring Bean的生命周期（非常详细）: <http://www.cnblogs.com/zrtqsk/p/3735273.html>    
* 3.计算机网络中的同步和异步.      
  计算机网络-步传输和异步传输（理解）: <http://blog.csdn.net/thisispan/article/details/7481127>
* 4.服务器的多线程和IO复用的应用场景，IO复用是什么复用?       
 ` 1) 多线程的应用场景: `     
 ` (1) 线程间有数据共享，并且数据是需要修改的（不同任务间需要大量共享数据或频繁通信时）； `     
 ` (2) 提供非均质的服务（有优先级任务处理）事件响应有优先级； `        
 ` (3) 任务并行计算，在非CPU Bound的场景下提高响应速度，降低时延； `     
 ` (4) 与人有IO交互的应用，良好的用户体验（键盘鼠标的输入，立刻响应）. `      
 ` 2) IO复用的应用场景: `       
 ` (1) 当客户处理多个描述字时（交互式输入以及网络接口），必须使用IO复用;  `     
 ` (2) 一个客户同时处理多个套接口; `    
 ` (3) 一个tcp服务程序既要处理监听套接口，又要处理连接套接口，一般需要用到IO复用; `   
 ` (4) 如果一个服务器既要处理TCP，又要处理UDP，一般也需要用到IO复用; `    
 ` (5) 如果一个服务器要处理多个服务或者多个协议，一般需要用到IO复用。 `     
 `  linux提供了select、poll、epoll等方法来实现IO复用. `    
 ` 3)IO复用: 单个线程，通过记录跟踪每个I/O流(sock)的状态，来同时管理多个I/O流。 `
* 5.进程和线程的概念，进程间通信的方式，消息队列和共享内存的适用场景.      
` 1) 进程与线程的一个简单解释: ` <http://www.ruanyifeng.com/blog/2013/04/processes_and_threads.html>        
  ` 2) 进程间通信的方式:  `        
  `  进程间8种通信方式:  `       
  `  (1) 无名管道(pipe)：管道是一种半双工的通信方式，数据只能单向流动，而且只能在具有亲缘关系的进程间使用。 `      
  `   进程的亲缘关系通常是指父子进程关系。   `    
  `  (2) 高级管道(popen)：将另一个程序当做一个新的进程在当前程序进程中启动，则它算是当前程序的子进程，这种方式我们成为高级管道方式。  `       
  `  (3) 有名管道(named pipe)：有名管道也是半双工的通信方式，但是它允许无亲缘关系进程间的通信。     `     
  `  (4) 消息队列(message queue)：消息队列是由消息的链表，存放在内核中并由消息队列标识符标识。消息队列克服了信号传递信息少、管道只能承载无格式字节流以及缓冲区大小受限等缺点。    `      
  `  (5) 信号量(semophore)：信号量是一个计数器，可以用来控制多个进程对共享资源的访问。它常作为一种锁机制，防止某进程正在访问共享资源时，其他进程也访问该资源。因此，主要作为进程间以及同一进程内不同线程之间的同步手段。  `         
  `  (6) 信号 (sinal)：信号是一种比较复杂的通信方式，用于通知接收进程某个事件已经发生。   `      
  `  (7) 共享内存(shared memory) ：共享内存就是映射一段能被其他进程所访问的内存，这段共享内存由一个进程创建，但多个进程都可以访问。共享内存是最快的 IPC 方式，它是针对其他进程间通信方式运行效率低而专门设计的。它往往与其他通信机制，如信号量配合使用，来实现进程间的同步和通信。  `        
  `  (8) 套接字(socket)：套接口也是一种进程间通信机制，与其他通信机制不同的是，它可用于不同机器间的进程通信。  `         
  ` 3) 消息队列和共享内存的适用场景: ` <http://www.cnblogs.com/biyeymyhjob/archive/2012/11/04/2753535.html> 
* 6.数据库的优化，索引为什么用B树，有什么好处？     
  B树在数据库索引中的应用剖析：<http://www.idouba.net/about-btrees-application-in-database-index-in-programmer/>        
  深入浅出空间索引：为什么需要空间索引: <http://www.cnblogs.com/LBSer/p/3392491.html>
   