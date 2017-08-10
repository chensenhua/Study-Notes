##1. ThreadThread本身是一个Thread，由Thread创建消息循环而来
```
     Looper.prepare();
        synchronized (this) {
            mLooper = Looper.myLooper();
            notifyAll();
        }
        Process.setThreadPriority(mPriority);
        onLooperPrepared();//消息队列创建前回调，重写该方法可以对handler进行初始化
        Looper.loop();
```

##2. 使用ThreadHandler消息循环可以使用


```
Handler handler=new Handler(HandlerThread.getLooper(),Handler.Callback);

Handler handler=new Handler(HandlerThread.getLooper());
将looper传递给handler
```
##3、操作
操作|意义
--|--|
start() |开启消息线程|
quit()|退出消息线程|
quitSafely()|安全退出消息线程，针对在消息队列中还有消息或者是延迟发送的消息没有处理的情况，调用这个方法后都会被停止掉|
getThreadId() |获取当前线程id|
getLooper()|获取消息looper|
