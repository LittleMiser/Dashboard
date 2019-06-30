# API 文档
## 2. 快递订单 
### 2.1 创建快递任务
> POST /createExpress/createExpress

例如：
```
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
```
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
```
{
    "id": "0e3dwudhi53hdieyf78",
    "user": "2"
}
```

### 2.4 完成快递任务
> POST /manageExpress/finish

例如：
```
{
    "id": "0e3dwudhi53hdieyf78",
    "user": "2"
}
```

### 2.5 删除快递任务
> POST /manageExpress/delete

例如：
```
{
    "id": "0e3dwudhi53hdieyf78",
    "user": "1"
}
```

### 2.6 取消快递任务
> POST /manageExpress/cancel

例如：
```
{
    "id": "0e3dwudhi53hdieyf78",
    "user": "2"
}
```