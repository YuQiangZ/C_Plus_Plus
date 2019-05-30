## **张量**（tensor）

`Tensor("add:0",shape=(2,),dtype=float32)`  

> add:0  "node:src_output"node为节点的名称，src_output表示当前张量来自节点的第几个输出。
>
> shape(2,)  **shape参数的个数应为维度数，每一个参数的值代表该维度上的长度**
>
> 第几个维度的长度，就是**左数第几个中括号组之间的元素总数量**  
>
> **注：左边有几个中括号就是几维**
>
> type 代表类型：每个张量会有唯一类型
>
> 

##  会话（session）

1. 第一种模式需要明确调用绘画生成函数和关闭会话函数 

   ```python
   # 创建一个会话
   sess=tf.Sesion
   # 使用创建好的会话来得到关心的运算结果
   sess.run()
   #关闭会话使得本次运行中使用的资源可以被释放。
   sess.close()
   ```

2. 第二种模式通过Python的上下文管理器来使用会话

   ```python
   #创建一个会话，并通过python中的上下文管理器来管理这个会话。只要将所有的计算放在“with”的内部就可以。当上#下文管理器退出时候会自动释放所有资源。
   with tf.Session as sess:
       sess.run()
   ```

