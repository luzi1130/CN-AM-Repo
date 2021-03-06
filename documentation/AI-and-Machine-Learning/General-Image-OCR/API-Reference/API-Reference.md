# 通用文字识别

## 一、接口描述 

### 1. 功能描述  

  基于业界领先的深度学习技术，利用光学字符识别技术，将图片上的文字转换为可编辑的文本，为您提供场景丰富、的整图文字检测和识别服务
  
### 2. 接口数据要求：  
> 1. 图片格式：jpg、jpeg、png
> 2. 图片大小：小于1M 

### 4. 接口使用：  
  平台为每个API提供试用体验服务，您在AI市场选择“免费试用”规格下单后，即可开始体验业内领先的人工智能API服务。
免费试用服务具有调用量、QPS限制，如需更高性能的API服务，可以提交咨询工单，联系京东AI扩容购买。

在获得使用权限后，您可使用已经封装好的SDK/参照[接口鉴权](https://aidoc.jd.com/user/auth.html)规则进行相应开发，整体流程详见   [接入流程](https://aidoc.jd.com/user/flow.html)  

## 二、请求说明
### 1. 接口地址 ：

```
https://aiapi.jd.com/jdai/ocr_universal
```
### 2. 请求方式：  
https  `post`aiapi.jd.com/jdai/ocr_universal
### 3. 请求参数    
#### （1）query请求参数  
公共请求参数  

名称 | 类型 | 必填 | 示例值	| 描述
------|------|-----|-----|-----
appkey | String | 是 | 80d2b762ecb86593f9668526920f46c	 | 您的appkey，可在买家中心控制台中获取  
timestamp | long | 是 | 1541491668060 | 请求的时间戳，精确到毫秒，timestamp有效期5分钟  
sign | String | 是 | 2e148773a0337a8f2200ba90d445f083	 | 签名，根据规则MD5(sectetkey,timestamp)， 

#### （2）header请求参数
业务请求参数

名称 | 类型 | 必填 | 示例值 | 描述
------|-----|-----|-----|-----
Content-Type | String | 是 | image/jpg | 标准编码格式

#### （3）body请求参数
业务请求参数

名称 | 类型 | 必填 | 示例值 | 描述
------|-----|-----|-----|-----
无 | binary | 是 | 无 | 图片内容，传入图片

### 4、请求代码示例
建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的4接口使用

## 三、返回说明
### 1、返回参数
#### （1）公共返回参数  

名称 | 类型 | 示例值 | 描述
------|-----|-----|-----
code | string | 1001 | 参见下方错误码-系统级错误码
charge | boolean | false 或 true | false：不扣费， true：扣费
remain | long | 1305 | 按天计算剩余调用次数
msg | string | 查询成功 | 参见下方错误码-系统级错误码
result | object | {...} | 查询结果

#### （2）业务返回参数
result参数信息

名称 | 类型 | 示例值 | 描述
------|-----|-----|-----
code|	int|	0|	参照四、错误码-业务错误码
message|	string|	success|	状态码描述
request_id|	string|	cb4f53b8c60e9589445cc4cd895cf5b6|	为方便定位问题的32位uuid
resultData|	object|	{...}|	返回识别结果

resultData参数信息

名称 | 类型 | 示例值 | 描述
------|-----|-----|-----
location | String | {"x":151,"width":90,"y":72,"heigth":30} | 检测区域
text | String | 经济实惠 | 识别结果

### 2、返回示例   


```
{
    "code": 0,
    "resultData": [
        {
            "location": {
                "x": 151,
                "width": 90,
                "y": 72,
                "height": 30
            },
            "text": "每一"
        },
        {
            "location": {
                "x": 279,
                "width": 360,
                "y": 72,
                "height": 30
            },
            "text": "小细节 体现人性化设计"
        },
        {
            "location": {
                "x": 179,
                "width": 93,
                "y": 179,
                "height": 31
            },
            "text": "十一"
        },
        {
            "location": {
                "x": 636,
                "width": 87,
                "y": 177,
                "height": 33
            },
            "text": "2)"
        },
        {
            "location": {
                "x": 51,
                "width": 104,
                "y": 260,
                "height": 16
            },
            "text": "经济实惠"
        },
        {
            "location": {
                "x": 181,
                "width": 134,
                "y": 260,
                "height": 17
            },
            "text": "12档强度调节"
        },
        {
            "location": {
                "x": 343,
                "width": 106,
                "y": 260,
                "height": 17
            },
            "text": "1小时充电"
        },
        {
            "location": {
                "x": 490,
                "width": 96,
                "y": 260,
                "height": 17
            },
            "text": "7级*保障"
        },
        {
            "location": {
                "x": 611,
                "width": 136,
                "y": 259,
                "height": 18
            },
            "text": "2年免费质保"
        },
        {
            "location": {
                "x": 50,
                "width": 106,
                "y": 284,
                "height": 17
            },
            "text": "不换刷头"
        },
        {
            "location": {
                "x": 180,
                "width": 128,
                "y": 283,
                "height": 18
            },
            "text": "减少不适感"
        },
        {
            "location": {
                "x": 332,
                "width": 117,
                "y": 284,
                "height": 17
            },
            "text": "使用450次"
        },
        {
            "location": {
                "x": 480,
                "width": 106,
                "y": 284,
                "height": 17
            },
            "text": "安全防水"
        },
        {
            "location": {
                "x": 588,
                "width": 182,
                "y": 284,
                "height": 16
            },
            "text": "品牌信誉 优质服务"
        },
        {
            "location": {
                "x": 177,
                "width": 349,
                "y": 370,
                "height": 11
            },
            "text": "*数据来源:SGS报告: SHES150600318501-FOREO LUNA IPX."
        },
        {
            "location": {
                "x": 537,
                "width": 82,
                "y": 371,
                "height": 10
            },
            "text": "FOREO INC"
        }
    ],
    "message": "success",
    "request_id": "815774d6ed6ca43e5d0cce316d36d822"
}

```

