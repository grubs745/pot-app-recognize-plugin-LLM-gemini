# Pot-App LLM 文字识别插件
## 说明
修改了过时的模型列表，fork from [OpenAI](https://github.com/pot-app/pot-app-recognize-plugin-openai)
## usage
填入API和API Endpoint，Endpoint的逻辑为：
```js
if (!requestPath) {
        requestPath = "https://api.openai.com";
    }
    if (!/https?:\/\/.+/.test(requestPath)) {
        requestPath = `https://${requestPath}`;
    }
    if (requestPath.endsWith('/')) {
        requestPath = requestPath.slice(0, -1);
    }
    if (!requestPath.endsWith('/chat/completions')) {
        requestPath += '/v1/chat/completions';
    }
```
可以自行理解，请求的模板当然是OpenAI兼容格式。
## input为自填
提供一些参考：
- `Pro/Qwen/Qwen2-VL-7B-Instruct`
  建议走硅基流动，￥0.35/1M tokens，而且这家有活动，邀请注册直接送￥14，浅浅贴个[#aff](https://cloud.siliconflow.cn/i/P5hlopKQ)。
- `claude-3-haiku-20240307`
  一般中转价格为 ￥0.25/1M tokens，但是`Anthropic`时不时抽风就很烦。