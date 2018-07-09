# Netty_heartbeat
 心跳检测的概念

 在分布式架构中，比如Hadoop集群，Storm集群等，或多或少都涉及到Master/Slave的概念，
 往往是一个或者多个Master和N个Slave之间进行通信。那么通常Master应该需要知道Slave的
 状态，Slave会定时的向Master进行发送消息，相当于告知Master：“我还活着，我现在在做什么，
 什么进度，我的CPU/内存情况如何”等，这就是所谓的心跳。Master根据Slave的心跳，进行协调，
 比如Slave的CPU/内存消耗很大，那么Master可以将任务分配给其他负载小的Slave进行处理；比如
 Slave一段时间没有发送心跳过来，那么Master可能会将可服务列表中暂时删除该Slave，并可能发
 出报警，告知运维/开发人员进行处理

 ## 注意点
 - 使用sigar.jar 需要把lib下的.dll 文件加到%java_home%/bin 目录下
 否则会报错