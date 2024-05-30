# 抽象类
+ Name() 返回此策略的名称
+ CreateFilter(const Slice* keys, int n,
                            std::string* dst)用户提供的已排序的一组键keys,大小为n，增加到dst中
+ KeyMayMatch(const Slice& key, const Slice& filter) 判断key是否在列表中如果在返回true，否则可能true或false         


NewBloomFilterPolicy(int bits_per_key) 新建布隆过滤器