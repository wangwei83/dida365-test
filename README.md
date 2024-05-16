# dida365-test

https://web.postman.co/

谷歌邮箱登录

文档：
https://developer.dida365.com/docs#/openapi
首先创建：

第一步接口配置：
https://dida365.com/oauth/authorize?scope=tasks:write tasks:read&client_id=rE1Sv62USQuIoTs5af&state=state&redirect_uri=https://www.baidu.com/&response_type=code


第二步：
https://dida365.com/oauth/authorize?scope=tasks:write tasks:read&client_id=rE1Sv62USQuIoTs5af&state=state&redirect_uri=https://www.baidu.com/&response_type=code在浏览器中运行
地址栏返回如：https://www.baidu.com/?code=Zcy6Gd&state=state



第三步：
https://dida365.com/oauth/token
认证：输入appsetting中的basic auth, 输入第二步返回的code（如Zcy6Gd）。
返回值如：
```python

{
    "access_token": "65b89ec8-ed1b-4e52-9e47-e7a5cf80743a",
    "token_type": "bearer",
    "expires_in": 15520438,
    "scope": "tasks:read tasks:write"
}
```

下一步解决普通接口的调用。
目前也咨询了技术、飞扬、令涛

## 获取所有project
https://dida365.com/open/v1/project/

使用 Postman 设置授权
1. 打开 Postman。
2.选择你要测试的请求。
3.进入"Authorization"选项卡。
4.在"Type"下拉菜单中选择"Bearer Token"。
5.在"Token" 输入框中输入你的访问令牌。来自第三步
6.发送请求。

返回值如：
```python

[
    {
        "id": "6483b3ca414c9108d37c11ae",
        "name": "家事",
        "color": "#930000",
        "sortOrder": -824633786368,
        "kind": "TASK"
    },
    {
        "id": "66454737eb96f60000000043",
        "name": "成信",
        "color": "transparent",
        "sortOrder": -824902221824,
        "viewMode": "list",
        "kind": "TASK"
    }
]
```

## 用上一条中的id获得对应的project
https://dida365.com/open/v1/project/66454737eb96f60000000043
返回值如：
```python

{
    "id": "66454737eb96f60000000043",
    "name": "成信",
    "color": "transparent",
    "sortOrder": -824902221824,
    "viewMode": "list",
    "kind": "TASK"
}
```
## 用上一条中的id获得进一步的project详细信息
https://dida365.com/open/v1/project/66454737eb96f60000000043/data
返回值如：
```python

{
    "project": {
        "id": "66454737eb96f60000000043",
        "name": "成信",
        "color": "transparent",
        "sortOrder": -824902221824,
        "viewMode": "list",
        "kind": "TASK"
    },
    "tasks": [
        {
            "id": "66454843eb96f6000000004d",
            "projectId": "66454737eb96f60000000043",
            "sortOrder": 0,
            "title": "毕业设计20级推进",
            "timeZone": "Asia/Shanghai",
            "isAllDay": true,
            "priority": 0,
            "status": 0,
            "columnId": ""
        },
        {
            "id": "664549ffeb96f6000000005c",
            "projectId": "66454737eb96f60000000043",
            "sortOrder": -268435456,
            "title": "工程实践1-3-5推进",
            "content": "",
            "desc": "",
            "timeZone": "Asia/Shanghai",
            "isAllDay": true,
            "priority": 0,
            "repeatFlag": "",
            "status": 0,
            "columnId": ""
        }
    ],
    "columns": []
}
```
