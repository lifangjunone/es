## 聚合
##### 示例
- method: GET
- url: http://127.0.0.1:9200/shopping/_search
- 参数
1. 根据指定字段分组
```json
{
  "aggs": {  // 聚合函数
    "price_group": {  // 名称，随意起名
      "terms": { // 分组
        "field": "price"  //　分组字段
      }
    }
  },
  "size": 0 // 返回结果中移除原始数据
}
```
2. 根据指定字段求平均值
```json
{
  "aggs": {
    "price_avg": {
      "avg": { // 求平均值
        "field": "price"
      }
    }
  },
  "size": 0
}
```