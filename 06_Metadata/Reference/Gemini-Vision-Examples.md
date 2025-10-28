# Gemini Vision 使用示例

本文件展示如何配置和使用 Google Gemini Vision 进行图片和文档分析。

## 配置状态

✅ **已配置** - API Key 已设置，MCP 服务器运行正常

## 可用命令

- `mcp__gemini-vision__analyze_image` - 分析单张图片
- `mcp__gemini-vision__extract_text` - OCR文字提取
- `mcp__gemini-vision__compare_images` - 比较图片
- `mcp__gemini-vision__suggest_image_filename` - 生成描述性文件名
- `mcp__gemini-vision__analyze_document` - 分析文档

## 使用示例

### 1. 图片内容分析

```bash
# 分析截图
"请分析 05_Attachments/screenshot.png 这张图片，
告诉我它显示了什么界面或信息。"

# 分析照片
"分析 05_Attachments/photo.jpg 中的主要元素
和场景内容。"
```

### 2. 文字提取 (OCR)

```bash
# 提取图片中的文字
"请提取 05_Attachments/sign.png 中的所有文字内容。"

# 处理文档
"提取 05_Attachments/document.pdf 中的完整文本。"
```

### 3. 图片比较

```bash
# 比较两张图片的差异
"比较 05_Attachments/before.png 和 05_Attachments/after.png
之间的主要差异。"

# 找出相似性
"分析 05_Attachments/design1.jpg 和 05_Attachments/design2.jpg
的相似之处和不同点。"
```

### 4. 智能重命名

```bash
# 批量重命名
"请为 05_Attachments/ 文件夹中的所有图片
根据内容建议更好的文件名。"

# 单个文件重命名
"为 05_Attachments/IMG_1234.jpg 建议一个描述性的文件名。"
```

### 5. 文档分析

```bash
# PDF内容总结
"分析 05_Attachments/report.pdf 的主要内容
并提取关键信息。"

# 表格数据提取
"从 05_Attachments/sheet.pdf 中提取表格数据。"
```

## 实际应用场景

### 🔍 调试和开发
- 分析错误截图
- 提取日志文件内容
- 比较UI设计稿

### 📚 研究和学习
- 提取论文PDF内容
- 分析图表和数据
- 整理手写笔记

### 🏢 工作效率
- 处理发票和收据
- 分析会议白板照片
- 整理名片信息

## 注意事项

1. **文件路径**：使用相对于vault根目录的路径
2. **文件大小**：建议单个文件不超过10MB
3. **API限制**：免费版每分钟15次请求
4. **隐私**：敏感文件请注意隐私保护

## 故障排除

**"找不到文件"**：
- 检查文件路径是否正确
- 确认文件存在于 05_Attachments/ 文件夹

**"API限制"**：
- 等待一分钟后重试
- 考虑升级API计划

**"分析失败"**：
- 检查文件格式是否支持
- 确认网络连接正常

---

*最后更新：2024-10-28*