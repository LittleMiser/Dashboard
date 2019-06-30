# API 文档
## 2. 快递订单 
### 2.1 创建快递任务
> POST /createExpress/createExpress

例如：
```javascript
[
    {
        "user": "1",
        "contact" : "张三",
        "phone" : "13111111111",
        "payment" : 2,
        "due_date" : 2019-6-30,
        "location" : "广州-广州-番禺区",
        "pickup_address" : "菜鸟驿站",
        "delivery_address" : "慎思园5号",
        "description" : "小件",
        "isRecepted": false,
        "isFinished": false,
        "recept_user": ""
    }
]
```

### 2.2 获取全部快递（未领取）
> GET /getExpress/get  

例如：
```javascript
[
    {
        "user": "2",
        "contact" : "张三",
        "phone" : "13111111111",
        "payment" : 2,
        "due_date" : 2019-6-30,
        "location" : "广州-广州-番禺区",
        "pickup_address" : "菜鸟驿站",
        "delivery_address" : "慎思园5号",
        "description" : "小件",
        "isRecepted": false,
        "isFinished": false,
        "recept_user": ""
    }
]
```

### 2.3 领取快递任务
> POST /expressDetail/takeExpress

例如：
```javascript
{
    "id": "0e3dwudhi53hdieyf78",
    "user": "2"
}
```

### 2.4 完成快递任务
> POST /manageExpress/finish

例如：
```javascript
{
    "id": "0e3dwudhi53hdieyf78",
    "user": "2"
}
```

### 2.5 删除快递任务
> POST /manageExpress/delete

例如：
```javascript
{
    "id": "0e3dwudhi53hdieyf78",
    "user": "1"
}
```

### 2.6 取消快递任务
> POST /manageExpress/cancel

例如：
```javascript
{
    "id": "0e3dwudhi53hdieyf78",
    "user": "2"
}
```

## 3.问卷任务

### 3.1 创建问卷

> POST /createWJ/post_wj

例如：

```javascript
{
    "_id" : ObjectId("5d14e4c3b497ee7ec876619d"),
    "creator" : "\"13111111111\"",
    "title" : "11",
    "questions" : [ 
        {
            "title" : "aa",
            "ans_a" : "b",
            "ans_b" : "v",
            "ans_c" : "x",
            "qtype" : 0
        }, 
        {
            "title" : "ttt",
            "ans_a" : "1",
            "ans_b" : "2",
            "ans_c" : "3",
            "qtype" : 1
        }
    ],
    "answer" : [],
    "total_bonus" : 9,
    "every_pay" : 9,
    "remain" : 0,
    "deadline" : "September 27, 2019"
}
```

### 3.2 搜索问卷

* 按`title`搜索

  > POST /getQuestion/search_title

  例如：

  ```javascript
  {
     "title" : "11"
  }
  ```

* 按`creator`搜索

  > POST /manageQuestion/search_creator

  例如：

  ```javascript
  {
    "creator" : "\"13111111111\""
  }
  ```

### 3.3 填写问卷

> POST /WJinfo/fill_in

例如：

```javascript
{
  "_id" : ObjectId("5d14e4c3b497ee7ec876619d"),
  "answer" : [ 
        {
            "ans_a" : 0,
            "ans_b" : 1,
            "ans_c" : 0
        }, 
        {
            "ans_a" : 1,
            "ans_b" : 0,
            "ans_c" : 1
        }
    ]
}
```

### 3.4 删除问卷

> POST /manageQuestion/delete_wj

例如：

```javascript
{
  "_id" : ObjectId("5d14e4c3b497ee7ec876619d")
}
```


