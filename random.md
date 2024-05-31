# 随机数类 (Random)
## 私有成员
+ uint32_t seed_ 种子
## 公有成员
### 构造函数
(uint32_t s) 传入种子
+ uint32_t Next() 返回一个随机数
+ uint32_t Uniform(int n) 返回$[0, n)$的值
+ bool OneIn(int n)  在约 $\frac{1}{n}$ 的情况下返回 true，否则返回 false
+ uint32_t Skewed(int max_log) 返回max_log 位的随机数