## query
##### 查询地址
- method:　GET
- url: http://127.0.0.1:9200/shopping/_search/
##### 查询参数
  1. 全量查询 + 分页 + 字段过滤 + 指定字段排序
      ```json
          {
            "query": {
              "match_all": {  // 查询所有
              }
            },
            "from": current_page * per_page_size,
            "size": per_page_size,
            "_source": ["title"],  // 过滤需要的字段
            "sort": {   // 根据 price 字段的逆序排序
              "price": {
                "order": "desc"
              }
            }
          }
      ```
     **示例**
     ```json
        {
          "query": {
            "match_all": {
            }
          },
          "from": 0,
          "size": 2,
          "_source": ["title"],
          "sort": {
            "price": {
              "order": "asc"
            }
          }
        }
2. 多条件组合查询
- AND (must)
```json
    {
      "query" : {
        "bool": {
          "must": [
            {
              "match": {
                "category": "小米"
              }
            },
            {
              "match": {
                "price": "39999.00"
              }
            }
          ]
        }
      }
    }
```
- OR (should)
```json
    {
      "query" : {
        "bool": {
          "should": [
            {
              "match": {
                "category": "小米"
              }
            },
            {
              "match": {
                "category": "华为"
              }
            }
          ]
        }
      }
    }
```
3. 单条数据通过 _id　查询
- method:　GET
- url: http://127.0.0.1:9200/shopping/_doc/{_id}
- url: http://127.0.0.1:9200/shopping/_doc/pEwbaYcBwDNBeR_zNnwP
