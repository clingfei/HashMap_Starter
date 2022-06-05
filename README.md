# HashMap

## CS106L: Standard C++ Programming 

### Implementation
- hashmap拥有一个私有成员`_buckets_array`, 其中储存了一系列buckets
- 每个bucket是一个链表，由`node`组成
- 每个`node`保存了一个key-value对，在`node`结构中，这个pair是`value_type`类型的字段值，`value_type`是`std::pair<K, M>`的类型别名
- 在查找或插入一个key时，HashMap首先通过hash函数将key转换为一个int，hash函数保存在私有成员变量`_hash_function`中，在STL中拥有默认的hash函数。然后HashMap使用这个整数mod`_buckets_array`中的bucket数量，结果为HashMap中插入或查找的下标位置。最后只需要遍历这个下标所指示的链表找到与之对应的key。
- HashMap有时需要增大buckets的数量，并且将原有的bucket重新hash来保证每个key对应的链表中没有太多的结点。

### Code Structure
- hashmap.h:包含不完整的类函数原型以及对于每个函数的注释。需要修改其中的某些私有函数原型，但不应该修改共有的函数类型
- hashmap.cpp:包含了HashMap的实现以及实现细节的注释。在修改milestone1的函数签名之外，还需要添加milestone2的实现
- hashmap_iterator.h:包含了HashMapIterator的声明和实现，该文件不需要修改。Importantly,需要清楚`hashmap.h`中`iterator`和`const_iterator`的区别
- short_answer.txt:将结果写入到该文件
- build.sh:编译指令
- main.sh:HashMap的示例代码
- test.cpp和test_settings.cpp:测试代码