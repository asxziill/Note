# 字符串类
支持字符串或字符数组构造
+ data 返回数据指针
+ size 返回字符大小
+ empty 返回是否为空
+ 重载[] 
+ clear 清空
+ remove_prefix(size_t n) 移除前缀长度n
+ ToString 返回字符串
+ compare(Slice x) 返回与x比较的结果 <0
  //   <  0 iff "*this" <  "b",
  //   == 0 iff "*this" == "b",
  //   >  0 iff "*this" >  "b"
+ starts_with(Slice x) 是否以x为前缀