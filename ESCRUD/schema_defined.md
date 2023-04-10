## schema 定义
##### 示例
- method: PUT
- http://127.0.0.1:9200/user/_mapping
- params:
```json
    {
      "properties": {
        "name": {
          "type": "text",
          // 文本格式，可以进行分词
          "index": true
          // 表示该字段建立索引
        },
        "sex": {
          "type": "keyword",
          // 表示关键字字段，不容许进行分词　
          "index": true
          // 表示给该字段建立索引
        },
        "tel": {
          "type": "keyword",
          "index": false
        }
      }
    }
```
##### 案例
１．创建 index
- POST http://127.0.0.1:9200/user
2. 定义　schema (mapping)
- POST http://127.0.0.1:9200/user/_mapping
- 参数：
```json
    {
      "properties": {
        "name": {
          "type": "text",
          // 文本格式，可以进行分词
          "index": true
          // 表示该字段建立索引
        },
        "sex": {
          "type": "keyword",
          // 表示关键字字段，不容许进行分词　
          "index": true
          // 表示给该字段建立索引
        },
        "tel": {
          "type": "keyword",
          "index": false
        }
      }
    }
```
３．创建测试数据
- POST http://127.0.0.1:9200/user/_create/00001
```json
    {
        "name": "小米",
        "sex": "男",
        "tel": "18621282783"
    }
```
4. 检索数据
- GET http://127.0.0.1:9200/user/_search
- 参数
```json
    {
        "query": {
            "match": {
                "sex": "男的"
            }
        }
    }
```