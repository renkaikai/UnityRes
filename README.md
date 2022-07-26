# UnityRes
Res Module

## 预备知识

- 程序集
- 序列化
- 资源加载方式

## 打包

- AssetBundleConfig
- CRC32

## 加载/卸载

- 类对象池/资源对象池作用？
    - 类对象池使用  GetOrCreate 需要new某个类的时候 直接调Pool的Spawn 减少频繁new

- ClassObjectPool

- ObjectManager

- AssetBundleManager
    - 读取AssetBundle配置表
    - 设置中间类新新引用计数
    - 根据路径加载AssetBundle
    - 根据路径卸载AssetBundle
    - 为ResourceManager提供加载中间类，根据中间类释放资源，查找中间类等方法

- ResourceManager
    - 以双向链表为基础的资源池
        - 为何使用双向链表？[双向链表也叫双链表，是链表的一种，它的每个数据结点中都有两个指针，分别指向直接后继和直接前驱。所以，从双向链表中的任意一个结点开始，都可以很方便地访问它的前驱结点和后继结点]
            我们希望频繁使用的处于容器的最顶端，不经常使用单位资源处于容器下面，这样当内存达到峰值的时候从下面开始清
            头部尾部相关操作复杂度为O(1)
    - 基础资源同步加载
    - 基础资源异步加载
    - 基础资源卸载
    - 清空缓存
    - 预加载
    - 为ObjectManager提供同步异步资源加载
