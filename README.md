# SnapMemo
Deepseek-api-based iOS Shortcut for taking screenshots and create memo or calendar events.

[![iOS](https://img.shields.io/badge/iOS-16+-blue.svg)](https://developer.apple.com/ios/)
[![iPadOS](https://img.shields.io/badge/iPadOS-16+-blue.svg)](https://developer.apple.com/ipados/)
[![DeepSeek](https://img.shields.io/badge/DeepSeek-API-black)](https://platform.deepseek.com/)

> 截屏 → 自动识别活动/任务 → 一键生成日历日程或备忘录  
> 基于 DeepSeek API，低成本、高可控，全部在 iOS 快捷指令（iOS Shortcut）中运行。

---

##  <a id="ChineseVer"></a>

###  核心功能

- **智能识别**：对截屏内容进行分析，自动区分“有明确时间的活动/任务”与“无截止时间的待办事项”。
- **自动创建日程**：若识别到活动起止时间、地点等信息，将自动在系统日历中创建日程，时间、地点填入对应字段，其他重要信息附在备注中。
- **自动创建备忘录**：对于没有明确截止时间的任务，直接生成一条备忘录，方便后续查阅。
- **批量处理与手动确认**：一张截图中包含多个活动或任务时，会先列出待创建条目列表，您可以通过勾选/取消勾选来控制生成哪些项目。
- **创建前可编辑**：在最终写入日历前，允许您确认并手动修改时间、地点等关键信息，确保准确无误。

###  优势

- **成本极低**：本场景无需顶尖大模型，使用 DeepSeek 等平价 API，单次调用成本远低于 Notion AI 等方案。
- **高度可定制**：相较于Todoo等现成软件，您可以自由修改快捷指令中的提示词、模型、默认日历/文件夹，甚至通过自制副快捷指令扩展新的输出类型。

###  不足

- **展示能力有限**：日程和备忘录的查看依赖系统日历、备忘录及其小组件，不如 Notion 或 Todoo 的自定义视图丰富。
- **隐私风险**：截图内容会通过 API 发送至第三方模型服务商（DeepSeek），虽然我们不存储任何数据，但无法完全避免模型训练风险。**涉及敏感信息的截图请谨慎使用，建议手动脱敏后再操作。**

###  系统要求与依赖

- **设备**：iOS / iPadOS 16 及以上
- **API**：有效的 DeepSeek API Key（可在 [platform.deepseek.com](https://platform.deepseek.com/) 注册获取）
- **工具**：Apple 快捷指令 App（系统内置）

###  使用方法

1. **下载快捷指令**  
   - 方式一：点击 [iCloud 分享链接-主快捷指令](https://www.icloud.com/shortcuts/aba28e7a92184d13b9a6084543f3ba18)、[iCloud分享链接-备忘录](https://www.icloud.com/shortcuts/f9076021ffb4405f9b8903b75fabec07) 、[iCloud分享链接-日历](https://www.icloud.com/shortcuts/4a8c4ce373854bd98f95b64e2ac2f4ee)、[iCloud分享链接-列表多选](https://www.icloud.com/shortcuts/1803e9d03af749ac8e5606b1681f29da)分别下载4个快捷指令。  
   - 方式二：将本仓库中的 4 个 `.shortcut` 文件下载到手机，保存到“文件” App，然后在文件中点击每个文件，导入到快捷指令 App。

2. **配置 API Key**  
   - 打开主快捷指令(Snapmemo-zh)，找到 `API Key` 对应的文本输入框，粘贴您在 DeepSeek 平台获取的 Key。  
   - 默认模型为 `deepseek-v4-flash`（价格低廉），如需更换模型或供应商，请同时修改 `model` 和 `url` 参数。  
   - 注意：本快捷指令**不依赖**多模态能力，纯文本识别即可。

3. **设置默认日历与备忘录文件夹（可选）**  
   - 默认日程会写入系统“个人”日历，默认备忘录存放在“备忘录”主文件夹。  
   - 如需更改，请打开“建立日程”快捷指令，按提示修改日历名称；在主快捷指令中可修改备忘录文件夹名称。

4. **唤起使用**  
   - 将主快捷指令设置为侧边栏按钮(进入设置app-点击“操作按钮”设置-左右翻动找到“快捷指令”-选择“SnapMemo_zh”)。  
   - 长按侧边栏按钮即可启动。

5. **错误处理**
   - 当调用大模型API的过程出现异常时，快捷指令会自动保存错误信息与出错前的用户请求内容（保存位置自选），以便排查问题。
   - 如要获取更多调试信息，可以设置DebugMode=True，快捷指令会保存过程中的请求、模型的完整回复与思维链、具体的工具调用过程等，以便排查问题。

###  后续计划

- **时间语义增强**：当前无法理解“下周二”等相对时间。计划增加当前时间获取与推算逻辑（临时解决方案：若截图来自微信聊天，可点击消息时间显示完整日期，模型可据此推算）。
- **多轮交互**：虽然已支持工具调用，但不支持与用户的多轮对话。后续将把“选择题”和“填空题”以工具（Tools）形式暴露给智能体，实现交互式补全。
- **更多功能**：增加“添加提醒事项”、“识别重复日程”、“日程开始前设置提醒”等能力。


