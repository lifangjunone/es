## 精准匹配
##### 示例
- method: GET
- url http://127.0.0.1:9200/shopping/_search
- 参数：
```json
    {
      "query": {
        "match_phrase": {
          "category": "小米"
        }
      }
    }
```
##### 高亮显示
```json
    {
      "query": {
        "match_phrase": {
          "category": "小米2"
        }
      },
      "highlight": {  // 高亮　category　字段
          "fields": {
              "category": {}
          }
      }
    }
```