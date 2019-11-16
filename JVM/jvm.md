## 1.谈谈JVM内存？

## 2.哪些情况会出现OutOfMemoryException 和 StackOverflowException
-   OutOfMemoryException   
    -   内存中加载的数据量过于庞大，如一次从数据库取出过多数据；
    -   集合类中有对对象的引用，使用完后未清空，使得JVM不能回收；
    -   代码中存在死循环或循环产生过多重复的对象实体；
    -   使用的第三方软件中的BUG；
    -   启动参数内存值设定的过小；
-   StackOverflowException
    -   递归层数超过JVM限制    

## 3.JVM调优

## 4.GC垃圾回收算法有哪些？