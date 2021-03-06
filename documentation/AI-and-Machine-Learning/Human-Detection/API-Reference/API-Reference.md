# 人体检测

----------

## 一、接口描述 

### 1.功能描述
人体检测API主要用于对传入的图片中所有人体的位置进行检测，返回其坐标值以及置信度。

### 2. 接口使用 
平台为每个API提供试用体验服务，您在AI市场选择“免费试用”规格下单后，即可开始体验业内领先的人工智能API服务。
免费试用服务具有调用量、QPS限制，如需更高性能的API服务，可以提交咨询工单，联系京东AI扩容购买。

在获得使用权限后，您可使用已经封装好的SDK/参照[接口鉴权](https://aidoc.jd.com/user/auth.html)规则进行相应开发，整体流程详见   [接入流程](https://aidoc.jd.com/user/flow.html)  

### 3.图片要求

> 1. 图片格式：jpg、jpeg、png
> 2. 图片像素尺寸：最小 256\*256 像素，最大 4096\*4096 像素
> 3. 图片文件大小：小于2M

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jd.com/jdai/human_detect
未上线时地址：http://192.168.0.135:8000/human_detect
```

### 2. 请求方式：
  
https `post` aiapi.jd.com/jdai/human_detect_chanchuangyun

### 3. 请求参数  
 
#### （1）query请求参数  
公共请求参数  
<table>
   <tr>
      <th>名称</th>
      <th>类型</th>
      <th>必填</th>
      <th>示例值</th>
      <th>描述</th>
   </tr>
   <tr>
      <td>appkey</td>
      <td>string</td>
      <td>是</td>
      <td>80d2b762ecb86593f9668526920f46c</td>
      <td>您的appkey，可在买家中心控制台中获</td>
   </tr>
   <tr>
      <td>timestamp</td>
      <td>long</td>
      <td>是</td>
      <td>1541491668060</td>
      <td>请求的时间戳，精确到毫秒，timestamp有效期5分钟</td>
   </tr>
   <tr>
      <td>sign</td>
      <td>string</td>
      <td>是</td>
      <td>2e148773a0337a8f2200ba90d445f083</td>
      <td>签名，根据规则MD5(sectetkey,timestamp)</td>
   </tr>
</table>

#### （2）header请求参数
业务请求参数
<table>
   <tr>
      <th>名称</th>
      <th>类型</th>
      <th>必填</th>
      <th>示例值</th>
      <th>描述</th>
   </tr>
   <tr>
      <td>Content-Type</td>
      <td>string</td>
      <td>是</td>
      <td>application/octet-stream</td>
      <td>表示在发送到服务器之前，所有字符都会进行编码。</td>
   </tr>
</table>

#### （3）body请求参数
业务请求参数
<table>
   <tr>
      <th>名称</th>
      <th>类型</th>
      <th>必填</th>
      <th>示例值</th>
      <th>描述</th>
   </tr>
   <tr>
      <td>无</td>
      <td>binary</td>
      <td>是</td>
      <td>采用二进制方式读取图片</td>
      <td>图片内容，传入图片</td>
   </tr>
</table>

### 4、请求代码示例
建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的2接口使用
 
## 返回说明

### 1、返回参数
#### （1）公共返回参数

<table>
   <tr>
      <th>名称</th>
      <th>类型</th>
      <th>示例值</th>
      <th>描述</th>
   </tr>
   <tr>
      <td>code</td>
      <td>string</td>
      <td>1000</td>
      <td>参见下方错误码-系统级错误码</td>
   </tr>
      <tr>
      <td>charge</td>
      <td>boolean</td>
      <td>false 或 true</td>
      <td>false：不扣费， true：扣费</td>
   </tr>
      <tr>
      <td>remain</td>
      <td>long</td>
      <td>1305</td>
      <td>按天计算剩余调用次数</td>
   </tr>
      </tr>
      <tr>
      <td>msg</td>
      <td>string</td>
      <td>查询成功</td>
      <td>参见下方错误码-系统级错误码</td>
   </tr>
      </tr>
      <tr>
      <td>result</td>
      <td>object</td>
      <td>{...}</td>
      <td>查询结果</td>
   </tr>
</table>

#### （2）业务返回参数

<table>
   <tr>
      <th>名称</th>
      <th>类型</th>
      <th>示例值</th>
      <th>描述</th>
   </tr>
   <tr>
      <td>status</td>
      <td>int</td>
      <td>0</td>
      <td>返回结果，0表示成功，非0为对应错误号</td>
   </tr>
   <tr>
      <td>message</td>
      <td>string</td>
      <td>ok</td>
      <td>错误信息</td>
   </tr>
   <tr>
      <td>used_time</td>
      <td>int</td>
      <td>198</td>
      <td>整个请求花费的时间，单位为毫秒</td>
   </tr>
   <tr>
      <td>request_id</td>
      <td>string</td>
      <td>1544940159.6349967</td>
      <td>便于双方定位问题</td>
   </tr>
   <tr>
      <td>humanDetectionResult</td>
      <td>array</td>
      <td>[[x1,y1,x2,y2,score],[x1,y1,x2,y2,score],...]</td>
      <td>x1,y1,x2,y2,score分别表示预测出的人体矩形框的左上角坐标，右下角坐标，以及置信度。返归的矩形框按照置信度高低排序，当未检测到人体时，返回空array[]。</td>
   </tr>
</table>
 

### 2、返回示例

```Json
{
    "code": 10000, 
    "charge": false,
    "remain": 97,
    "msg": "查询成功",
    "result": 
    {
    	"status":0,
    	"request_id": "1544940159.6349967",
        "message":"ok",
        "used_time":95,
        "humanDetectionResult":
        [
            [319, 170, 395, 302, 1.0],
            [265, 173, 324, 295, 1.0],
            [265, 127, 314, 261, 0.96]
        ]    
    }
}
```
