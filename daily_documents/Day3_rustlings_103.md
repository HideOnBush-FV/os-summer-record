# 今日完成
## rustlings 103 实现二叉搜索树
### 困难

我自己的实现方式，本来是 while 到 fp.null ，这样就需要多一个指针（lp）来表示空的父节点，便于插入新节点。
写了N个小时报了一大堆错

- 两个指针就会报错不能同时多可变引用啦
- 一个可变一个不可变的话，更新 lp 的时候就会说不能是可变引用啦
- 只留一个指针，while 条件加上 fp.left/right 非空，就会由于unwrap报错所有权转移导致更新节点时不能用

### 解决

还是看了其他满分大佬的代码，学习了几个rust特性，参考了大佬们的思路

> 重点：使用递归而非迭代，规避所有权问题


# 知识点

Option 的几个方法

- as_mut() ：&mut Option<T> -> Option<&mut T>.
- as_ref() ： &Option<T> -> Option<&T>.
- as_deref_mut() ： Option<T> (or &mut Option<T>) to Option<&mut T::Target>

前面题目里用到的时候只是按照提示修改，没有细究功能和用法