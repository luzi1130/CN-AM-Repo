# 词法分析

## 一、接口描述 

### 1. 功能描述
提供中文分词、词性标注、命名实体识别三个功能，解析自然语言中的基本语言元素，并赋予词性，进一步将文本中的特定类型的事物名称或符号识别出来，使机器能更准确的理解内容，支撑自然语言的准确理解。

### 2. 接口使用 
平台为每个API提供试用体验服务，您在AI市场选择“免费试用”规格下单后，即可开始体验业内领先的人工智能API服务。
免费试用服务具有调用量、QPS限制，如需更高性能的API服务，可以提交咨询工单，联系京东AI扩容购买。

在获得使用权限后，您可使用已经封装好的SDK/参照[接口鉴权](https://aidoc.jd.com/user/auth.html)规则进行相应开发，整体流程详见   [接入流程](https://aidoc.jd.com/user/flow.html)  


## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jd.com/jdai/lexer_chanchuangyun
```

### 2. 请求方式：
  
https `post` aiapi.jd.com/jdai/lexer_chanchuangyun

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
      <td>application/json</td>
      <td>表示请求JSON格式的文本信息</td>
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
      <td>appId</td>
      <td>string</td>
      <td>否</td>
      <td>0</td>
      <td>应用id，同一调用方可以创建多个应用。appId不填或者为0时表示使用通用的分词模型。</td>
   </tr>
   <tr>
      <td>text</td>
      <td>string</td>
      <td>是</td>
      <td>克林顿访问中国</td>
      <td>输入文本</td>
   </tr>
   <tr>
      <td>type</td>
      <td>int</td>
      <td>是</td>
      <td>0</td>
      <td>选择所需的词法分析的结果，包括"分词"、"词性标注"和"命名实体识别”一个或多个的组合。<br>
      0: 提供分词，词性标注以及命名实体识别的结果<br/>
      1: 提供分词的结果<br/>
      2: 提供分词和词性标注的结果<br/>
      3: 提供分词和命名实体的结果<br/>
      如输入其它数值，默认按0情况处理</td>   
   </tr>
</table>

### 4、请求代码示例
建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的2接口使用


## 三、返回说明
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
      <td>参照四、错误码-业务错误码</td>
   </tr>
      <tr>
      <td>message</td>
      <td>string</td>
      <td>ok</td>
      <td>参照四、错误码-业务错误码</td>
   </tr>
      <tr>
      <td>request_id</td>
      <td>string</td>
      <td>5893465d31284468a8014de6ee430f8e</td>
      <td>便于双方定位问题</td>
   </tr>
   <tr>
      <td>text</td>
      <td>string</td>
      <td>克林顿访问中国</td>
      <td>输入文本</td>
   </tr>
   <tr>
      <td>tokenizedText</td>
      <td>list</td>
      <td> [{"offset": 0,"pos": "NR","length": 3,"ner": "PERSON","word": "克林顿"},...] </td>
      <td>词法分析结果，详情下面tokenizedText字段说明</td>
   </tr>
</table>

#### tokenizedText字段说明
<table>
   <tr>
      <th>名称</th>
      <th>类型</th>
      <th>示例值</th>
      <th>描述</th>
   </tr>
   <tr>
      <td>word</td>
      <td>string</td>
      <td>克林顿</td>
      <td>分词</td>
   </tr>
   <tr>
      <td>pos</td>
      <td>string</td>
      <td>NR</td>
      <td>词性</td>
   </tr>
   <tr>
      <td>ner</td>
      <td>string</td>
      <td>PERSON</td>
      <td>命名实体识别</td>
   </tr>
   <tr>
      <td>offset</td>
      <td>int</td>
      <td>0</td>
      <td>距离起始位置偏移</td>
   </tr>
   <tr>
      <td>length</td>
      <td>int</td>
      <td>3</td>
      <td>分词长度</td>
   </tr>
</table>

 
### 2、返回示例    


```
{
    "code": "10000",
    "charge": false,
    "remain": 97,
    "msg": "查询成功",
    "result": {
        "status": 0,
        "request_id": "ac7be2c2-c5c6-4bd4-b52d-e03b03fc5b58",
        "message": "ok",
        "text": "克林顿访问中国",
        "tokenizedText": [
            {
                "offset": 0,
                "pos": "NR",
                "length": 3,
                "ner": "PERSON",
                "word": "克林顿"
            },
            {
                "offset": 3,
                "pos": "VV",
                "length": 2,
                "ner": "O",
                "word": "访问"
            },
            {
                "offset": 5,
                "pos": "NR",
                "length": 2,
                "ner": "GPE",
                "word": "中国"
            }
        ]
    }
}
```
