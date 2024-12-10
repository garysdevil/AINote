# Prompt 
- 学习资料
    - https://learningprompt.wiki/docs/chatgpt-learning-path
    - https://github.com/Acmesec/PromptJailbreakManual/
    - https://github.com/dair-ai/Prompt-Engineering-Guide

## 基本
### 基本使用
1. Prompt 里最好包含完整的信息。
2. Prompt 最好简洁易懂，并减少歧义。
3. Prompt 要使用正确的语法、拼写，以及标点。
### 使用场景
1. 简单问答模式。精确、具体。
2. 根据例子回答问题。
```
Suggest three names for a horse that is a superhero.

Animal: Cat
Names: Captain Sharpclaw, Agent Fluffball, The Incredible Feline
Animal: Dog
Names: Ruff the Protector, Wonder Canine, Sir Barks-a-Lot
```
3. 推理/推断。
4. 写代码。
5. 文本转换
6. 解释。
7. 信息总结。
8. 信息提取。

## 高级
### Prompts 框架
1. Basic Prompt Framework
    1. Instruction（required）： The specific task you want the model to perform.
    2. Context（optional）： Background information providing context to guide better responses.
    3. Input Data (optional): Data for the model to process.
    4. Output Indicator (optional): Specifies desired output type or format.
2. CRISPE Prompt Framework
    1. CR： Capacity and Role - The role for ChatGPT to take on.
    2. I： Insight - Background info and context (I think Context is clearer).
    3. S： Statement - What you want ChatGPT to do.
    4. P： Personality - Desired style or manner for responses.
    5. E： Experiment - Ask for multiple answers.

### Zero-Shot Prompts 零样本提示
- Zero-Shot Chain of Thought
### Few-Shot Prompting 少量样本提示
- Few-Shot Chain of Thought

## 技巧
1. 减少耗时的问答
    1. 通过提示 `DO NOT ASK FOR INTERESTS. DO NOT ASK FOR PERSONAL INFORMATION.` ，来让AI不再追求问题的精确化。
2. 提供例子
    1. 如果我们的需求很难通过语言进行描述，则可以通过提供类似例子的方式，将信息传递给AI，以此来获取问题答案。
3. 添加引导词
4. 增加角色
    1. 答案的输出，可以有不同的表达方式，不同的人理解水平不平，因此可以在Prompt里增加一个角色。
    2. 例如`你是一位小学老师` 或 `请以小学老师的语言能里表达出答案`
5. 将指令和需要处理的文本分开
    1. 例如
        ```txt
            Please summarize the following sentences to make them easier to understand.
            Text: """具体内容"""
        ```
6. 通过格式词阐述需要输出的格式
    ```txt
        Use the following format:
        Text: <text to summarize>
        Summary: <summary>
        Translation: <summary translation>
        Names: <list of names in Italian summary>
        Output JSON: <json with summary and num_names>
    ```
7. Zero-Shot Prompts 零样本提示
8. Few-Shot Prompting 少量样本提示



## 正确的提问
```
问题？
内容: '内容'
输出格式？
```