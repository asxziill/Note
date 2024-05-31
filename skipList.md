# 跳表SkipList
模板 key, Comparator
## 私有
+ Node
+ int GetMaxHeight() 获取当前跳表的最大高度
+ Node* NewNode(const Key& key, int height)创建一个新节点
+ int RandomHeight()随机生成一个高度，用于确保跳表的平衡性
+ bool Equal(const Key& a, const Key& b)比较两个键是否相等
+ bool KeyIsAfterNode(const Key& key, Node* n)检查一个键是否在某个节点之后
+ Node* FindGreaterOrEqual(const Key& key, Node** prev)找到大于或等于某个键的节点
+ Node* FindLessThan(const Key& key)找到小于某个键的节点
+ Node* FindLast()找到最后一个节点
+ Comparator const compare_; 比较器
+ Arena* const arena_ 内存池
+ Node* const head_ 头指针
+ std::atomic<int> max_height_ 最大的高度
+ Random rnd_ 
+ enum { kMaxHeight = 12 } 最大高度
## 公有
### 基本函数
构造函数(Comparator cmp, Arena* arena) 比较器和内存池
**删除** 复制
### 方法
+ void Insert(const Key& key) 插入一个键值
+ bool Contains(const Key& key) 检查是否包含某个键值
+ class Iterator 迭代器


# 节点(Node)
## 构造函数
(const Key& k) 传入key
## 公有成员
+ Key const key 节点键值
+ Node* Next(int n) 获取第 n 层的下一个节点
+ void SetNext(int n, Node* x) 设置第 n 层的下一个节点
+ Node* NoBarrier_Next(int n) 无屏障操作的 Next 函数
+ void NoBarrier_SetNext(int n, Node* x) 无屏障操作的SetNext 函数
## 私有成员
+ std::atomic<Node*> next_[1]

# 迭代器 (Iterator)
## 公有成员
### 构造函数
(const SkipList* list) 跳表类

+ bool Valid() 检查迭代器是否指向一个有效节点
+ const Key& key() 返回当前节点的键值
+ void Next() 移动到下一个节点
+ void Prev() 移动到上一个节点（通过在列表中重新查找）
+ void Seek(const Key& target) 寻找大于或等于目标键的节点
+ void SeekToFirst() 定位到第一个节点
+ void SeekToLast() 定位到最后一个节点
## 私有成员
+ const SkipList* list_ 跳表
+ Node* node_ 当前指向的节点

指定空间new(多出来的空间不会初始化)
```C++
void* mem = ...; // 已分配的内存块
MyClass* obj = new (mem) MyClass(constructor_args);
```