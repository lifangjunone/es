## 更新
### 完全覆盖性修改(全量数据的更新)
> 幂等性，使用　PUT 方法
##### 示例
- method: PUT
- url: http://127.0.0.1:9200/shopping/_doc/{_id}
- url: http://127.0.0.1:9200/shopping/_doc/00001
```json
    {
        "title": "**手机",
        "category": "**",
        "images": "http://www.gulixueyuan.com/xm.jpg",
        "price": 39999.00
    }
```
### 局部性修改（局部数据更新）
> 局部数据的更新，每次更新的结果都是不相同的，非幂等，所以只能用　POST 方法
##### 示例
- method: POST
- url: http://127.0.0.1:9200/shopping/_update/{_id}
- url: http://127.0.0.1:9200/shopping/_update/00001
```json
    {
      "doc": {
        "title": "**xxx手机"　　// 需要修改的字段名
      }
    }
```
