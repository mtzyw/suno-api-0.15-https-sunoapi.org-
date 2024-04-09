# 提供标准的suno api服务。0.15一次
提供标准的suno api服务。0.15一次
欢迎注册免费送suno api额度 免费调用 

https://sunoapi.org/

回调URL
封面、标题、歌词生成完成回调
成功生成封面、标题、歌词后，我们将回调您在生成接口中提供的“回调地址”。

回调方法为“POST”，“Content-Type”设置为：“application/json”。

参数如下：

  {
    "code": 200,
    "msg": "成功",
    "data": {
      "callbackType": "text",
      "data": [
        {
          "audio_url": "音频url",
          "image_url": "封面url",
          "prompt": "歌词",
          "model_name": "模型名",
          "title": "音乐名称",
          "tags": "标签",
          "createTime": "2024-04-02 09:55:38"
        }
      ]
    }
  }
第一个音频生成完成回调
成功生第一个音频后，我们将回调您在生成接口中提供的“回调地址”。

回调方法为“POST”，“Content-Type”设置为：“application/json”。

参数如下：

  {
    "code": 200,
    "msg": "成功",
    "data": {
      "callbackType": "first",
      "data": [
        {
          "audio_url": "音频url",
          "image_url": "封面url",
          "prompt": "歌词",
          "model_name": "模型名",
          "title": "音乐名称",
          "tags": "标签",
          "createTime": "2024-04-02 09:55:38"
        }
      ]
    }
  }
全部生成完成回调
成功生成完成后，我们将回调您在生成接口中提供的“回调地址”。

回调方法为“POST”，“Content-Type”设置为：“application/json”。

参数如下：

成功：

  {
    "code": 200,
    "msg": "All generated successfully.",
    "data": {
      "callbackType": "complete",
      "data": [
        {
          "audio_url": "音频url",
          "image_url": "封面url",
          "prompt": "歌词",
          "model_name": "模型名",
          "title": "音乐名称",
          "tags": "标签",
          "createTime": "2024-04-02 09:55:38"
        }
      ]
    }
  }
失败：

  {
    "code": 501,
    "msg": "Audio generation failed.",
    "data": {
      "callbackType": "complete",
      "data": [
        {
          "audio_url": "音频url",
          "image_url": "封面url",
          "prompt": "歌词",
          "model_name": "模型名",
          "title": "音乐名称",
          "tags": "标签",
          "createTime": "2024-04-02 09:55:38"
        }
      ]
    }
  }
音频生成接口
音频生成接口介绍

HEADER PARAMETERS
Authorization
required
string
Example: Bearer {apiKey}
apiKey

REQUEST BODY SCHEMA: application/json
启用customMode，禁用instrumental 参数则需要style、prompt、title, 启用customMode，启用instrumental 参数则需要style、title, 禁用customMode，启用instrumental 参数则需要prompt, 禁用customMode，禁用instrumental 参数则需要prompt,

style	
string
风格

prompt	
string
主题词

title	
string
音乐名称

customMode
required
boolean
是否自定义模式

instrumental
required
boolean
是否纯音乐

callBackUrl
required
string
回调地址

Responses
200
OK

400
参数错误

401
未认证

405
调用超出限制

500
内部服务器错误


POST
/api/v1/generate

Request samples
PayloadcurlJavaPythonGoRust
Content type
application/json

Copy
{
"style": "string",
"prompt": "string",
"title": "string",
"customMode": true,
"instrumental": true,
"callBackUrl": "string"
}
Response samples
200400401405500
Content type
application/json

Copy
{
"code": 200,
"msg": "success",
"data": null
}
