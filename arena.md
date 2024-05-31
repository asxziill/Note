# 内存池
## 公有方法
### 基本函数
构造函数：初始化 Arena 对象。
删除拷贝构造函数和赋值运算符：防止 Arena 对象被复制。
析构函数：销毁 Arena 对象，释放所有分配的内存块。
### 方法
+ char* Allocate(size_t bytes) 返回一个指向新分配的 bytes 字节大小内存块的指针
+ char* AllocateAligned(size_t bytes) 按 malloc 提供的正常对齐方式分配内存
+ size_t MemoryUsage() 返回由 Arena 分配的内存总量的估计值，使用原子操作以线程安全的方式获取
## 私有
+ char* AllocateFallback(size_t bytes) 在当前内存块不足以分配所需内存时调用，用于处理分配失败的情况。
+ char* AllocateNewBlock(size_t block_bytes) 分配一个新的内存块
+ char* alloc_ptr_ 指向当前内存块的指针，用于追踪下一个可分配内存的位置
+ size_t alloc_bytes_remaining_ 当前内存块剩余的可用字节数
+ std::vector<char*> blocks_ 存储所有已分配的内存块的指针数组
+ std::atomic<size_t> memory_usage_ 使用原子操作记录 Arena 分配的内存总量