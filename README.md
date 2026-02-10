1. 检出项目
```
git clone https://github.com/pfyangf/pfyangf.github.io.git
```
2. 安装依赖
```
npm i
```
3. 编写中文博文
在`i18n/zh-CN/docusaurus-plugin-content-blog/2026`目录下创建md文件, 文件名格式: `mm-dd-英文博客名.md`名称中的空格用中横线代替,如`01-15-ai-blockchain-security. md`
4. 翻译
将`amt.config.json`放到项目根目录,里面带有大模型key,不能提交到仓库中
```
{
    "apiKey": "sk-xx", # 大模型密钥 
    "modelType": "deepseek", # 大模型厂商
    "modelName": "deepseek-chat", # 模型名称
    "inputDir": "./i18n/zh-CN/docusaurus-plugin-content-blog/2026/", # 输入路径:中文博客路径
    "outputDir": "./blog/2026/" # 输出路径,英文博客路径
}
```
执行翻译
```
amt 文件名 目标语言 模型
amt 02-10-web3-security-checklist.md en deepseek
```

