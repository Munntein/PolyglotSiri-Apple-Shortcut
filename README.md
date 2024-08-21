# PolyglotSiri Apple Shortcut

[!GitHub stars](https://img.shields.io/github/stars/Munntein/PolyglotSiri-Apple-Shortcut?style=plastic)](https://github.com/Munntein/PolyglotSiri-Apple-Shortcut/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Munntein/PolyglotSiri-Apple-Shortcut?style=plastic)](https://github.com/Munntein/PolyglotSiri-Apple-Shortcut/network/members)
[![GitHub license](https://img.shields.io/github/license/Munntein/PolyglotSiri-Apple-Shortcut?style=plastic)](https://github.com/Munntein/PolyglotSiri-Apple-Shortcut/blob/main/LICENSE.md)

[中文介绍](https://github.com/Munntein/PolyglotSiri-Apple-Shortcut/blob/main/Readme-zh.md)

PolyglotSiri is based on [ChatGPT-Siri](https://github.com/Yue-Yang/ChatGPT-Siri) and enhances its multilingual and speech capabilities.

Now you can talk to siri with any languge. And siri responses  bilingually(English and Chinese as i set) with a more natural vocie. Now you can treat Siri as a foreign friend and practice language training with it.

In addition to the OpenAI chatGPT API, Three other REST APIs are used:

1. OpenAI Whisper API: used as an STT service which can handle multiple languages. Native Siri can only understand one language at a time.
2. Azure Language Cognitive API: used to recognize the language of text for later Azure TTS language configuration.
3. Azure TTS: using Azure TTS to replace iOS native ones, resulting in more natural-sounding voice.



## Shortchut Link
https://www.icloud.com/shortcuts/61bbd941bfce433cb9193d990a8f4004
<br>
(the previous shortcut link has an issue, the url suffix after endpoint "/text/analytics/v3.0/languages" of azure language service was lost by mistake)



## Configurition and Customization

0. First you have to apply for openai api and Azure cloud
   - login into OpenAI, https://platform.openai.com
   - login into Azure, https://portal.azure.com/
   - In Azure cloud, two resource needed, speech and language. Depoly them.
1. Fill your api keys in this shortcut.
   - you need two openai keys, one for whisper and the other for completion.
   - Fill in Azure tts and Azure language cognitive service Keys.
2. Substitute Azure service REST API urls. There are three of them, one for text language cognition, and  two for Azure TTS (aiming for bilingual voice support, you could customize more for mutiple language)
3. Customize Azure TTS params
   - language and voice setting,  in TTS request body,  customize your language and vocie setting. Find all vocie here, https://learn.microsoft.com/en-us/azure/cognitive-services/speech-service/language-support?tabs=tts#supported-languages
   - In TTS request header, you can specify the audio output quality “X-Microsoft-OutputFormat”. Find all audio outputs here, https://learn.microsoft.com/en-us/azure/cognitive-services/speech-service/rest-text-to-speech?tabs=streaming#audio-outputs
4. Specify mulit-language if statement
   - To make azure TTS support multi-languge vocie, we need to use Azure language cognition to recognize text language. And using if statements to make it using the corresponding TTS language engine when speaking. 



## Usage

1. Download the [shortcut](https://www.icloud.com/shortcuts/61bbd941bfce433cb9193d990a8f4004).
2. Simply tap the shortcut and let the magic happen.
3. The audio recording will stop after 15 seconds by default. You can stop it either by tapping or waiting for the countdown to end.
4. Wait for responce.



## Issues

This shortcut is somewhat useful for language learning, but it’s not perfect. There are some issues.

1. Why are two OpenAI keys necessary?

   - In my practice, using the same key to request whisper and completion APIs, within very few rounds, say 2 or 3, the token would reach the completion api limits. Seperating the API keys would solve the problem. However, I'm still not quite clear on the rules, why whisper API requests counts towards the completion token size. 

2. Since there are three APIs to be called, performance may not be particularly smooth - especially if you need a proxy to access those services.

3. It doesn’t support streaming output like many other text chatgpt projects. This, coupled with previous network issues, results in slower response times, particularly when ChatGPT generates longer replies.

4. **The most critial issue**, this shortcut cannot function well in vocie wake-up mode. I tried my best to debug it, while giving up at end. Looking forward someone could solve the issue.

5. The second imperfect aspect is that the voice input section cannot automatically stop; manual tapping or waiting for the countdown to finish is required instead.

   

   

## Acknowledge

1. [ChatGPT-Siri](https://github.com/Yue-Yang/ChatGPT-Siri) 


