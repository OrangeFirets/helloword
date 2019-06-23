## Flume

#### 	1 . 简介

​		flume是一个分布式的日志采集工具

#### 	2 . 运行机制

​		flume核心的角色agent  , 类似数据传递员 , 内部有三个组件 : 

​			1 . source : 采集组件 , 用于跟数据源对接

​			2 . channel : 传输通道组件  ,  连接source与sink ,数据传输

​			3 . sink : 下沉组件 , 用于往下一级agent发送数据或者往最终存储系统传递数据

​		注意  : flume采集到的数据包装成even的形式传递数据

​			   启动flume :bin/flume-ng  agent  -c  ./conf  -f  ./conf/spooldir.conf  -n  a1 -Dflume.root.logger=INFO,console 

#### 	3 . flume的采集策略

​		 设置flume的采集数据的频率  , 设置时间和文件大小控制策略

​		 文件127.9M时候采集

​		两个小时滚动一次

#### 	4 .  flume的监测

​		flume比较脆弱 , 一旦抛异常 , 就会停止工作

​		什么情况表示flume死掉了 ? 

​		如果源数据 , 没有变少 ,flume可能死掉了

​		如果目的地数据 , 没有增对 , flume可能死掉了

​		解决方案  :  

​			a . 我们写脚本 , 定时执行检测  , 检测源数据有没有减少 , 检测目的地数据有没有增多  , 杀掉flume . 重新启动

​			b  . 使用failover机制

​				

​		

​			