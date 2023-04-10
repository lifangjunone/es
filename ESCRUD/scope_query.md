## 范围查询
##### 示例
- method: GET
- url: http://127.0.0.1:9200/shopping/_search
- 查询参数
```json
    {
      "query": {
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
          ],
          "filter": {
            "range": {
              "price": {
                "gt": 5000
              }
            }
          }
        }
      }
    }
```