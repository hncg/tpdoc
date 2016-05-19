# 用户相关API接口文档

1. 登录

#### http method post

#### host/v1/login

    |参数名|类型|
    |phone|int[11]|
    |passwd|string[6:32]|

#### 返回示例


    {
        "code": 2,
        "message": "帐号或密码错误"
    }

    {
        "user": {
            "id": 2864,
            "userId": 0,
            "userAccount": "18074471987",
            "userEmail": "",
            "userPwd": "86e1e22eb2212fcf836d5dac7949ddaf",
            "userClassId": 1,
            "userLock": 0,
            "loginCount": 0,
            "userName": "",
            "userPhone": "",
            "userSex": "",
            "userArea": "",
            "userWexin": "",
            "userQQ": "",
            "userAddTime": "2016-05-10 11:43:27",
            "training_times": 1,
            "expired_time": "2016-05-11 10:52:38"
        },
        "sid": "5d2e27c12a00649bf82cbf52cae0296d1d2f6292"
    }

2. 注册

#### http method post

#### host/v1/register

    |参数名|类型|
    |phone|int[11]|
    |passwd|string[6:32]|
    |verify|int[6]|

#### 返回示例

    {
        "code": 1,
        "message": "ok"
    }

    {
        "code": 9,
        "message": "用户已经存在"
    }

3. 找回密码

#### http method post

#### host/v1/retrieve

|参数名|类型|
|phone|int[11]|
|passwd|string[6:32]|
|verify|int[6]|

#### 返回示例

    {
        "code": 1,
        "message": "ok"
    }

    {
        "code": 10,
        "message": "用户不存在"
    }

4. 获取问题

#### http method get

#### host/v1/user/{user_id}/qa

|参数名|类型|含义|
|class_id|in:1,2|科目一二，科目三四|

#### 返回示例
    [
        {
            "id": 108,
            "qaId": 32749938,
            "qaTypeId": 1,
            "qaClassId": 75286254,
            "qaChapter": 2,
            "qaTitle": "依照我国法律规定，消费者协会是依法成立的对商品和服务进行社会监督的保护消费者合法权益的（ ）",
            "qaContent": "|A_社会组织|B_非社团法人 |C_行政机关|D_仲裁机构",
            "qaAnswer": "A",
            "qaMeno": "点评：选A",
            "qaViews": 0,
            "qaScore": 1,
            "qaFileName": "ynTYXbdFtz",
            "qaAddTime": "0000-00-00 00:00:00"
        },
        ...
    ]



5. 发送验证码

#### http method post

#### host/v1/send_phone_perify

    |phone|int[11]|
    |temp_id|in:82522|

#### 返回示例

    {
        "code": 1,
        "message": "ok"
    }

    {
        "code": 5,
        "message": "短信发送失败,联系客服试试吧"
    }

6.记录分数

#### http method post

#### host/v1/user/{user_id}/score

|参数名|类型|含义|
|class_id|in:1,2|科目一二，科目三四|
|rank_score|numeric|所得分数|
|rank_time|numeric|做题时间|
|rank_count|numeric|做题个数|


#### 返回示例

    {
        "code": 1,
        "message": "ok"
    }

    {
        "code": 10,
        "message": "用户不存在"
    }


6.获取分数记录

#### http method get

#### host/v1/user/{user_id}/score

#### 返回示例

    [
        {
            "id": 240,
            "userId": 57134094,
            "qaClassId": 1,
            "rankId": 88736267,
            "rankScore": 2,
            "rankTime": 49,
            "rankCount": 6,
            "rankAddTime": "2015-02-05 11:05:13"
        },
        ...
    ]
