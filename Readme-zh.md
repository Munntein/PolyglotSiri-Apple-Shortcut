# PolyglotSiri 苹果快捷方式

PolyglotSiri 基于 [ChatGPT-Siri](https://github.com/Yue-Yang/ChatGPT-Siri) 并增强了其多语言和语音能力。

现在您可以用任何语言与 Siri 对话。而且 Siri 的响应是双语的（我设置为英文和中文），声音更加自然。现在您可以把 Siri 当作外国朋友，并与它进行语言训练。

除了 OpenAI chatGPT API，还使用了其他三个 REST API：

1. OpenAI Whisper API：用作 STT 服务，可处理多种语言。原生的 Siri 只能一次理解一种语言。

2. Azure Language Cognitive API：用于识别文本的语言以供后续 Azure TTS 语言配置使用。

3. Azure TTS：使用 Azure TTS 替换 iOS 原生 TTS，从而产生更自然的声音。

   

## 快捷方式链接

https://www.icloud.com/shortcuts/9bd65fdaf1714ce09f862253d3324086



## 配置和定制

0. 首先您需要申请 openai api 和 Azure cloud

   - 登录到 OpenAI, https://platform.openai.com


   - 登录到Azure, https://portal.azure.com/


   - 在Azure云中，需要两个资源，一个是speech一个是language。部署它们。


1. 在此快捷方式中填写您的API密钥。

   - 您需要两个 openai 密钥，一个用于 whisper，另一个用于 completion。


   - 填写 Azure tts 和 Azure language cognitive service Keys。


2. 替换Azure服务REST API URL。其中有三个，一个用于文本语言认知，另外两个用于Azure TTS（旨在支持双语音支持，您可以根据需要自定义更多的多种语言）

3. 自定义 Azure TTS 参数

   - 语言和声音设置，在TTS请求正文中自定义您的语言和声音设置。在此处查找所有声音 https://learn.microsoft.com/en-us/azure/cognitive-services/speech-service/language-support?tabs=tts#supported-languages


   - 在TTS请求头中，您可以指定“X-Microsoft-OutputFormat” 音频输出质量。在此处查找所有音频输出 https://learn.microsoft.com/en-us/azure/cognitive-services/speech-service/rest-text-to-speech?tabs=streaming#audio-outputs


4. 指定多种语言 if 语句

   - 要使 azure TTS 支持多种语言发音，则需要使用 Azure 语言认知来识别文本的语言，并使用 if 陈述式

   

## 使用方法

1. 下载 [快捷方式](https://www.icloud.com/shortcuts/9bd65fdaf1714ce09f862253d3324086)。

2. 点击快捷方式并等待魔法发生。

3. 默认情况下15秒后录制将停止。您可以通过点击或等待倒计时结束来停止它。

4. 等待响应。

   


## Issues
这个快捷方式对语言学习有一定的帮助，但并不完美。存在以下问题：

1. 为什么需要两个OpenAI密钥？

  - 在我的实践中，使用相同的密钥请求whisper和completion API，在很少的几轮内（比如2或3轮），token就会达到完成API限制。分离API密钥可以解决这个问题。然而，我还不太清楚规则是什么，为什么whisper API请求计入了完成token大小。

2. 由于需要调用三个API，性能可能不是特别流畅——尤其是如果您需要代理访问这些服务。

3. 它不支持像许多其他文本chatgpt项目那样的流式输出。这与之前的网络问题结合在一起，导致ChatGPT生成较长回复时响应时间较慢。

4. **最关键的问题**是：此快捷方式无法在语音唤醒模式下正常工作。我尽力进行了调试，并最终放弃了它。期待有人能解决这个问题。

5. 第二个缺陷方面是：语音输入部分不能自动停止；必须手动点击或等待倒计时结束。

   


## 感谢

1.[ChatGPT-Siri](https://github.com/Yue-Yang/ChatGPT-Siri)
