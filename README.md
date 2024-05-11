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
{
    "access_token": "65b89ec8-ed1b-4e52-9e47-e7a5cf80743a",
    "token_type": "bearer",
    "expires_in": 15520438,
    "scope": "tasks:read tasks:write"
}


下一步解决普通接口的调用。
目前也咨询了技术、飞扬、令涛