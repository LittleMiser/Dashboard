# 数据库设计
## 1. 概要
数据库包含用户表、快递订单表、问卷表

## 2. UML 建模
![database model](../images/db_design.png)

## 3. 具体设计

### User

```javascript
/* 1 */
{
    "_id" : ObjectId("5d14e451b497ee7ec876619b"),
    "Identity" : "student",
    "Contact" : "13111111111",
    "Code" : "111111",
    "NickName" : "1",
    "Name" : "1",
    "old" : "20",
    "StudentNum" : "1",
    "Sex" : "female",
    "Grade" : "2",
    "Major" : "2",
    "Money" : 4988,
    "__v" : 0
}
```

### Paper

```javascript
/* 1 */
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
    ],
    "total_bonus" : 9,
    "every_pay" : 9,
    "remain" : 0,
    "deadline" : "September 27, 2019"
}

```

### Express

```javascript
/* 1 */
{
    "_id" : ObjectId("5d18aedf155af533ef9d948a"),
    "user" : "\"13111111111\"",
    "contact" : "13111111111",
    "phone" : "13111111111",
    "payment" : 4,
    "due_date" : ISODate("2019-07-26T16:00:00.000Z"),
    "location" : "山西省-晋城市-龙港镇",
    "pickup_address" : "1",
    "delivery_address" : "1",
    "description" : "1",
    "isRecepted" : false,
    "isFinished" : false,
    "recept_user" : null,
    "__v" : 0
}
```


