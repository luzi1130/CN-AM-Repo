# 人脸搜索

----------

## 一、接口描述 

### 1.功能描述

人脸搜索也称为1：N识别，即在一个已有人脸集合中找出与指定人脸最相似的一张或多张人脸

### 2. 接口使用 
使用接口前，需要先完成API的下单购买，然后可使用已经封装好的SDK/参照[接口鉴权](https://aidoc.jd.com/user/auth.html)规则进行相应开发，整体流程详见   [接入流程](https://aidoc.jd.com/user/flow.html)  

### 3.图片要求

> 1. 图片格式：bmp, jpg, jpeg, png, jfif
> 2. 图片像素尺寸：最小 48\*48 像素，最大 4096\*4096 像素
> 3. 图片文件大小：小于2MB

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jd.com/jdai/faceSearch
```

### 2. 请求方式：
  
https `post` aiapi.jd.com/jdai/faceSearch

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

#### （2）body请求参数
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
      <td>groupId</td>
      <td>string</td>
      <td>否</td>
      <td>6979e9bd79b944b49e0d6e74079d5098</td>
      <td>分组Id</td>
   </tr>
   <tr>
      <td>groupName</td>
      <td>string</td>
      <td>否</td>
      <td>test</td>
      <td>分组名称,若groupId不为空则以groupId作为分组的唯一标识</td>
   </tr>
   <tr>
      <td>imageBase64</td>
      <td>string</td>
      <td>是</td>
      <td></td>
      <td>图片的Base64编码</td>
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
      <td>参见下方错误码-系统级错误码数</td>
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
      <td>Success</td>
      <td>返回错误信息</td>
   </tr>
   <tr>
      <td>result</td>
      <td>string</td>
      <td>Success</td>
      <td>返回人脸唯一标识faceId</td>
   </tr>
</table>
 


### 2、返回示例

```Json
{
    "status": 0, 
    "charge": false,
    "remain": 97,
    "msg": "查询成功",
		"result": "
			{\"faceSearchResults\":
				[{\"conf\":0.9999682,
						\"faceID\":
						{\"faceId\":\"771ff9c6668c4a538b7ec514fbffc97f\",\"index\":0,\"outerId\":\"fu2\",\"sim\":1.0},
						\"height\":1006.3228,
						\"left\":575.8482,
						\"top\":594.26544,
						\"width\":769.7747
				}]
			}",
    "requestid": "c34efa5cb8d040b6b641fc3e57404f87",
    "message": "success",
    "status": 0
}
```
## 四、错误码

### 1.系统级错误码
[详见返回码](https://aidoc.jd.com/user/returncode.html)  

### 2.业务错误码 

<table>
   <tr>
      <th>业务错误码（status）</th>
      <th>对应message说明</th>
      <th>说明</th>
   </tr>
   <tr>
      <td>12002</td>
      <td>1. "missing param" 2.groupId or groupName is null</td>
      <td>参数缺失.  1. 缺失参数 2.分组ID和分组名称都为空，两者不能均为空</td>
   </tr>
   <tr>
      <td>12003</td>
      <td>1."image base64 is invalid"</td>
      <td>解析参数错误。 1.图像Base64编码错误</td>
   </tr>
   <tr>
      <td>13111</td>
      <td>""image quality is bad""</td>
      <td>图像尺寸或者质量不符合标准，当图像尺寸超过4096 * 4096或者小于48 * 48时会报该错误</td>
   </tr>
   <tr>
      <td>13112</td>
      <td>"face quality is not stardard"</td>
      <td>人像质量不符合标准，当人脸姿态过大，人脸摇头，歪头，点头的角度超过30度会报该错误</td>
   </tr>
   <tr>
      <td>13134</td>
      <td>"face not found"</td>
      <td>找不到人脸，当图像中无法检测到人脸时会报该错误</td>
   </tr>
   <tr>
      <td>13303</td>
      <td>"time out"</td>
      <td>超时错误，当服务端请求负载过多会报该错误</td>
   </tr>
   <tr>
      <td>13312</td>
      <td>"groupId not found"</td>
      <td>分组Id不存在，需要搜索的组的Id不存在时会报该错误</td>
   </tr>
</table>