[toc]

# 0. 序言

下面制作一个简单的进度条



# 1. LoadSceneAsync使用

LoadSceneAsync可以异步的加载新场景。加载新场景时，原场景仍可以使用。

LoadSceneAsync返回一个AsyncOperation对象。

**AsyncOperation.progress**可以查询加载的进度，就是通过它来实现进度条。

借助Slider的部分参考血量条制作。



# 2. 注意事项

LoadSceneAsync加载场景分为两个阶段

第一阶段是加载场景到内存，这个过程progress**取值范围是0-0.9**；

第二阶段是Unity删除原来场景的Gameobject，导入新的场景，这个过程progress**取值范围是0.9-1**。



# 3. 报错修复

因为打开了编辑器里的Player Mode

重新加载场景时，可能因为缓存问题。导致异步加载场景速度过快，旧场景很快被删除。

代码中的协程被提前销毁了。造成空访问。只要关闭Player Mode就可以了。

![](PlayerMode.png)