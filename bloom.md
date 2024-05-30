# 辅助函数
uint32_t BloomHash(const Slice& key) 返回key的哈希值

# 布隆过滤器(BloomFilterPolicy)
## 公有
### 构造函数(int bits_per_key)
传入初始化参数
+ char* Name() 返回过滤器策略的名称
+ void CreateFilter(const Slice* keys, int n, std::string* dst) 大小为n的keys插入dst中
+ bool KeyMayMatch(const Slice& key, const Slice& bloom_filter) 检查布隆过滤器是否可能包含给定键
## 私有
+ bits_per_key_
+ k_


FilterPolicy* NewBloomFilterPolicy(int bits_per_key) 返回实例