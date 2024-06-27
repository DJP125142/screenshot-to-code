# screenshot-to-code 汉化版

一个简单的工具，使用人工智能将屏幕截图、实体模型和Figma设计转换为干净、实用的代码。现在支持Claude Sonnet 3.5 and GPT-4O！

https://github.com/abi/screenshot-to-code/assets/23818/6cebadae-2fe3-4986-ac6a-8fb9db030045

支持的框架:

- HTML + Tailwind
- React + Tailwind
- Vue + Tailwind
- Bootstrap
- Ionic + Tailwind
- SVG

[注：什么是Tailwind？](https://blog.csdn.net/snsHL9db69ccu1aIKl9r/article/details/111026790)

支持的AI模型:

- Claude Sonnet 3.5 - Best model!
- GPT-4O - also recommended!
- GPT-4 Turbo (Apr 2024)
- GPT-4 Vision (Nov 2023)
- Claude 3 Sonnet
- DALL-E 3 for image generation

更多演示请参见下面的[示例](#-示例)部分

我们还增加了录屏支持，用于录制网站运行中的视频/屏幕记录，并将其转化为功能原型。

![google in app quick 3](https://github.com/abi/screenshot-to-code/assets/23818/8758ffa4-9483-4b9b-bb66-abd6d1594c33)

[点击此处了解更多视频信息](https://github.com/abi/screenshot-to-code/wiki/Screen-Recording-to-Code).

[推特上关注我查看最新更新](https://twitter.com/_abi_).

## 赞助商

<a href="https://konghq.com/products/kong-konnect?utm_medium=referral&utm_source=github&utm_campaign=platform&utm_content=screenshot-to-code" target="_blank" title="Kong - powering the API world"><img src="https://picoapps.xyz/s2c-sponsors/Kong-GitHub-240x100.png"></a>

## 🚀 官网

[前往官网体验](https://screenshottocode.com).

## 🛠 入门指南

该应用前端使用 React/Vite & 后端使用 FastAPI. 

需要的密钥:

* [GPT-4 的 OpenAI API key](https://github.com/abi/screenshot-to-code/blob/main/Troubleshooting.md)
* Anthropic key (可选) - 只有当你需要使用 Claude Sonnet, 或者是需要使用录制能力时才需要.

后端部署 (使用 Poetry 做包管理 - 如果你没有安装可使用`pip install poetry` 安装poetry):

```bash
cd backend
echo "OPENAI_API_KEY=sk-your-key" > .env
poetry install
poetry shell
poetry run uvicorn main:app --reload --port 7001
```

如果要使用Anthropic，将`ANTHROPIC_API_KEY`添加到`backend/.env`中，也可以使用前端的设置对话框设置密钥(加载前端后点击齿轮设置图标)。

前端部署:

```bash
cd frontend
yarn
yarn dev
```

访问 http://localhost:5173 来使用本地应用.

如果你想修改端口号可以更新 `frontend/.env.local` 里的VITE_WS_BACKEND_URL.

调试模式下, 如果你不想浪费 GPT4-Vision credits, 可以在模拟模式下运行后端(这将流式传输预先录制的响应):

```bash
MOCK=true poetry run uvicorn main:app --reload --port 7001
```

## Docker

如果您的系统上安装了Docker，可以使用Docker部署，在根目录下运行:

```bash
echo "OPENAI_API_KEY=sk-your-key" > .env
docker-compose up -d --build
```

该应用程序将在 http://localhost:5173 启动并运行。请注意，您不能用这种设置开发应用程序，因为文件更改不会触发重新构建。


## 🙋‍♂️ 常见问题

- **我在设置后端时遇到了一个错误。我该怎么修？** [看看这个](https://github.com/abi/screenshot-to-code/issues/3#issuecomment-1814777959). 如果还不行，就提个issue.
- **如何获得OpenAI API密钥？** 参阅 https://github.com/abi/screenshot-to-code/blob/main/Troubleshooting.md
- **如何配置OpenAI代理？** - 如果您无法直接访问OpenAI API(由于国家限制等原因)，您可以尝试VPN，或者您可以将OpenAI基本URL配置为使用代理:在: `backend/.env` 里设置OPENAI_BASE_URL，或者直接在设置对话框的UI中设置。请确保URL的路径中包含“v1”，因此它应该是这样的:  `https://xxx.xxxxx.xxx/v1`
- **如何修改我的前端请求到的后端地址？** - 在front/.env.local中配置VITE_HTTP_BACKEND_URL和VITE_WS_BACKEND_URL例如设置VITE_HTTP_BACKEND_URL=http://124.10.20.1:7001
- **运行后端时看到UTF-8错误？** - 在windows上使用notepad++打开.env文件，然后设置编码格式选择UTF-8. 
- **我如何提供反馈？** 如需反馈、功能请求和错误报告，请在[Twitter](https://twitter.com/_abi_)上联系我.

## 📚 示例

**NYTimes**

| Original                                                                                                                                                        | Replica                                                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img width="1238" alt="Screenshot 2023-11-20 at 12 54 03 PM" src="https://github.com/abi/screenshot-to-code/assets/23818/3b644dfa-9ca6-4148-84a7-3405b6671922"> | <img width="1414" alt="Screenshot 2023-11-20 at 12 59 56 PM" src="https://github.com/abi/screenshot-to-code/assets/23818/26201c9f-1a28-4f35-a3b1-1f04e2b8ce2a"> |

**Instagram page (with not Taylor Swift pics)**

https://github.com/abi/screenshot-to-code/assets/23818/503eb86a-356e-4dfc-926a-dabdb1ac7ba1

**Hacker News** but it gets the colors wrong at first so we nudge it

https://github.com/abi/screenshot-to-code/assets/23818/3fec0f77-44e8-4fb3-a769-ac7410315e5d

## 🌍 托管版本

🆕 [前往试用 (付费)](https://screenshottocode.com). 或者参阅 [入门指南](#-getting-started) 以获得与您自己的API密钥一起使用的本地安装说明。
