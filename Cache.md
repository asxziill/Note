接口文件
定义了一个缓存接口 Cache
工厂函数 NewLRUCach

# Cache 
+ 构造函数：默认构造函数
+ 拷贝构造和赋值运算符 : 删除
## Handle
用于引用缓存中的条目

## 虚函数
+ Insert(const Slice& key, void* value, size_t charge,
                         void (*deleter)(const Slice& key, void* value))插入一个键值对到缓存中，并指定其容量消耗。返回一个句柄
+ Lookup(const Slice& key) 查找一个键的映射，返回一个句柄
+ Release(Handle* handle) 释放句柄 
+ Value(Handle* handle) 获取句柄中的值
+ Erase(const Slice& key) 如果缓存中包含给定键的条目，则将其删除
+ NewId() 返回一个新的数值 ID
+ Prune() 移除所有不再使用的缓存条目
+ TotalCharge() 返回所有存储在缓存中的元素的总容量消耗的估计值