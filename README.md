# Bright Data ChatGPT 搜索爬取器（Node.js）

[![Bright Data Promo](https://github.com/bright-cn/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://www.bright.cn/)


<a href="https://githubbox.com/bright-cn/bright-data-scrape-chatgpt-search-nodejs-project?file=index.py" target="_blank">在 CodeSandbox 打开</a>，使用 GitHub 登录，然后 fork 该仓库开始修改。

本项目提供一个简单的 Node.js 模板，使用 [Bright Data Web Scraper API](https://www.bright.cn/products/web-scraper/chatgpt) 爬取 [ChatGPT AI 搜索](https://www.bright.cn/products/web-scraper/chatgpt) 的结果。

---

## 目录

- [概述](#概述)
- [功能](#功能)
- [先决条件](#先决条件)
- [安装](#安装)
- [用法](#用法)
- [配置](#配置)
- [示例](#示例)
- [输出](#输出)
- [支持](#支持)
- [许可证](#许可证)

---

## 概述

该仓库演示如何使用 Bright Data Scraper API 触发并下载 ChatGPT AI 搜索结果。包含示例提示词以及用于批量与自定义搜索的工具函数。

---

## 功能

- 通过 Bright Data Scraper 的 `/trigger` API 端点触发 ChatGPT AI 搜索
- 使用 `/status` 端点监控进度
- 将结果下载并保存为 JSON

---

## 先决条件

- Node.js v16 或更高版本
- 拥有带 API KEY 的 Bright Data 账号

---

## 安装

```sh
git clone https://github.com/your-org/bright-data-scrape-chatgpt-search-nodejs-project.git
cd bright-data-scrape-chatgpt-search-nodejs-project
npm install
```

---

## 用法

1. 设置你的 Bright Data API Token

   编辑 [`index.js`](index.js) 并设置你的 API Token：
   ```js
   const API_TOKEN = 'YOUR_API_TOKEN_HERE';
   ```

2. 运行爬取脚本

   ```sh
   node index.js
   ```

   结果会以带时间戳的 `.json` 文件保存在项目目录中。

---

## 配置

- API Token：  
  在 Bright Data 控制台的账户设置中获取你的 API Token。

- 数据集 ID（Dataset ID）：  
  ChatGPT AI Search 的默认数据集 ID 已在 [`index.js`](index.js) 中设置好。

---

## 示例

### 运行示例搜索

脚本默认会执行三个示例提示词：
```js
const SAMPLE_SEARCHES = [
  { url: "https://chatgpt.com/", prompt: "Top hotels in New York", country: "" ],
  { url: "https://chatgpt.com/", prompt: "What are the biggest business trends to watch in the next five years?", country: "" ],
  { url: "https://chatgpt.com/", prompt: "Best practices for remote team management", country: "" }
];
```

### 自定义搜索

在 [`index.js`](index.js) 中取消注释并修改以下内容以运行你自己的提示词：
```js
const customSearch = [createSearch("Best programming languages to learn in 2024")];
const customResults = await searchChatGPT(customSearch);
await saveResults(customResults, 'custom_search.json');
```

### 批量搜索

```js
const multipleSearches = [
  createSearch("Climate change solutions"),
  createSearch("AI ethics guidelines"),
  createSearch("Sustainable business practices")
];
const multiResults = await searchChatGPT(multipleSearches);
await saveResults(multiResults, 'multiple_searches.json');
```

---

## 输出

- 结果将保存为 JSON 文件（例如 `chatgpt_results_YYYY-MM-DDTHH-MM-SS.json`）。
- 每个文件包含来自 Bright Data 的原始 API 响应。

---

## 支持

- [Bright Data 帮助中心](https://www.bright.cn/help)
- [联系支持](https://www.bright.cn/contact-us)

---

## 许可证

本项目基于 MIT 许可证发布。详情见 [LICENSE](LICENSE)。
