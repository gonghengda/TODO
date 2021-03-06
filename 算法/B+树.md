# 目录

- B+ 树特性   

```
1. 有k个子树的中间节点包含有k个元素(B树中是k-1个元素),每个元素不保存数据，只用来索引，所有数据都保存在叶子节点  
2. 所有的叶子节点中包含了全部元素的信息，及指向含有这些元素记录的指针，且叶子节点本身依关键字的大小自小而大顺序链接   
3. 所有的中间节点元素都同时存在于子节点，在子节点元素中是最大(或最小)元素
```

- B+树中，只有叶子节点带有卫星数据，其余中间节点仅仅是索引，没有任何数据关系.  

- 补充：在数据库的聚集索引(Clustered Index) 中，叶子节点直接包含卫星数据。在非聚集索引(NonClustered Index) 中，  
  叶子节点带有指向卫星数据的指针.  


- 和B- 树的不同：   
```
  1. B+树的中间节点没有卫星数据,索引同样大小的磁盘页可以容纳更多的节点元素,意味着在相同情况下,B+树的结构比B-树更加  
     矮胖，因此查询时IO次数更少  
  2. B+树查询必须最终查找到叶子节点，而B-树只要找到匹配的元素即可，无论匹配元素处于中间节点还是叶子节点。因此，B-树  
     的查找性能并不稳定(最好情况是只查根节点，最坏情况是查到叶子节点).而B+树的每一次查找都是稳定的  
```

- 总结：B+树优势:   
```
  1. IO次数更少   
  2. 查询性能更高   
  3. 范围查询简单   
```

- 应用:  
  Mysql ..