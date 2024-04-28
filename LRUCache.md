# LRUHandle 
+ value 自定义值
+ deleter(const Slice&, void* value) 自定义删除函数
+ next_hash 下一个的哈希值(用于哈希表的链表)
+ next 后一个节点(用于LRU双向链表的指针，下同)
+ prev 前一个节点
+ charge
+ key_length key长
+ in_cache 是否在缓存中
+ refs 引用次数
+ hash 哈希值
+ key_data 字符串
+ Slice key() 返回保存内容的字符

# 哈希表 (HandleTable)
返回指针的地址方便直接修改指针去重定向
#### 基本函数
+ 构造时为空
+ 析构主要析构 list_
+ 
#### 私有：
+ length_ 数组长度
+ elems_ 存储的元素数量
+ list_ LRUHandle指针数组
+ LRUHandle** FindPointer(const Slice& key, uint32_t hash) 找到key的位置,hash为key的哈希值，返回保存该LRUHandle指针的地址
+ void Resize()重新根据元素数量新增哈希表
#### 公有：
+ LRUHandle* Lookup(const Slice& key, uint32_t hash) 返回有key的hash值的节点指针
+ LRUHandle* Insert(LRUHandle* h)插入新节点h,返回同样信息的旧指针，如果没有则为old
+ LRUHandle* Remove(const Slice& key, uint32_t hash)移除表中的key，并返回被移除元素的指针

# LRU的实现LRUCache
#### 私有：
+ LRU_Remove(LRUHandle* e) 从链表中删除e
+ LRU_Append(LRUHandle* list, LRUHandle* e) 在list的前面插入e
+ Ref(LRUHandle* e) 增加e的计数
+ Unref(LRUHandle* e) 减少e的计数
+ FinishErase(LRUHandle* e) 清除e，返回e是否为空
+ capacity_ LRU的容量(一定要初始化)
+ mutex_ 互斥锁
+ usage_ 使用总花费
+ lru_ 双向链表
+ in_use_ 双向链表
+ table_ 哈希表
#### 公有：
+ SetCapacity(size_t capacity) 设置缓存容量
+ Cache::Handle* Insert(const Slice& key, uint32_t hash, void* value,
                        size_t charge,
                        void (*deleter)(const Slice& key, void* value));
+ Cache::Handle* Lookup(const Slice& key, uint32_t hash) 查看key，返回指针
+ void Release(Cache::Handle* handle); 释放指定的handle
+ void Erase(const Slice& key, uint32_t hash);
+ void Prune();
+ size_t TotalCharge() 返回usage_