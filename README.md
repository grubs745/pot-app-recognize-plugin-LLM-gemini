# Pot-App LLM 文字识别插件
## 说明
增加了对Gemini模型的支持，fork from [Ideenaster/pot-app-recognize-plugin-LLM](https://github.com/Ideenaster/pot-app-recognize-plugin-LLM)
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

    if (requestPath.includes('gemini')) {
        if (!requestPath.endsWith('/v1beta/openai')) {
            requestPath += '/v1beta/openai';
        }
        if (!requestPath.endsWith('/v1/chat/completions')) {
            requestPath += '/chat/completions';
        }
    } else {
        if (!requestPath.endsWith('/v1/chat/completions')) {
            requestPath += '/v1/chat/completions';
        }
    }
```
可以自行理解，请求的模板当然是OpenAI兼容格式。

由于Gemini模型只传入图片会出错，修改成customprompt同时也会在user content传入。
