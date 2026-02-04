# Xiaohongshu Recruiter (小红书招聘助手)

用于在小红书上发布高质量的 AI 相关岗位招聘帖子，包含自动生成极客风格的招聘封面图和详情图，并提供自动化发布脚本。

## 功能概述

本技能旨在帮助用户快速、专业地在小红书发布 AI 岗位的招聘信息。通过 "Systemic Flux" 设计理念生成符合极客审美的视觉素材，并提供 Playwright 脚本实现半自动化发布。

## 使用场景

- 发布 AI 相关岗位招聘信息
- 寻找 Agent 设计师
- 招聘其他 AI 领域人才
- 创建高质量的小红书招聘帖子

## 核心工作流

### 简化模式（默认）

当用户仅给出一句话指令（如"发布一个前端开发工程师的招聘信息到小红书"）时：

1. 模型自行补全招聘信息与文案
2. 自动补充默认投递方式（私信联系/评论联系）
3. 自动生成封面图与详情图
4. 自动打开浏览器，等待用户扫码登录
5. 自动填写图文信息并一键发布

### 完整工作流程

#### 1. 信息收集

收集以下关键信息（仅在用户明确要求或关键信息冲突时询问）：

- **岗位名称**（如：Agent Designer）
- **核心职责 & 要求**
- **投递邮箱**

#### 2. 生成视觉素材

使用本地脚本生成极客风格的招聘图片：

```bash
node scripts/generate_images.js
```

**产出文件**：
- `cover.png` - 封面图
- `jd_details.png` - 详情图

#### 3. 生成文案

生成符合小红书调性的文案，保存为 `post_content.txt`。

**文案规则**：
- 标题：少于 20 字
- 正文：包含话题标签
- 详细规则参考 `assets/rules.md`

#### 4. 自动化发布

使用 Playwright 脚本自动发布到小红书。

**前置要求**：

```bash
# 安装 Playwright
pip install playwright

# 安装浏览器驱动
playwright install chromium
```

**执行发布**：

```bash
python3 scripts/publish_xiaohongshu.py "你的标题" "post_content.txt" "cover.png" "jd_details.png"
```

**交互流程**：

1. 脚本打开小红书创作者中心
2. 若出现登录页，扫码登录
3. 登录完成后，脚本自动：
   - 上传图片
   - 填写标题与正文
   - 点击"发布"
4. 浏览器保持打开供用户确认

## 资源文件

### Assets（设计资源）

- **assets/design_philosophy.md** - 视觉设计哲学（Systemic Flux 设计理念）
- **assets/rules.md** - 详细的操作规范和平台限制

### Scripts（脚本工具）

- **scripts/generate_images.js** - 图片生成脚本
- **scripts/publish_xiaohongshu.py** - 发布自动化脚本

### References（参考文档）

包含额外的参考资料和指南

## 设计理念

采用 "Systemic Flux" 设计风格：
- 极客审美
- 科技感视觉
- 符合 AI 领域特色
- 专业且现代

## 技术要求

- Node.js（用于图片生成）
- Python 3.x
- Playwright 浏览器自动化库
- Chromium 浏览器驱动

## 注意事项

1. 首次使用需要扫码登录小红书账号
2. 确保网络连接稳定
3. 遵守小红书平台发布规则
4. 图片和文案需符合平台内容规范

## 使用示例

简单的一句话指令：

```
发布一个 Agent Designer 的招聘信息到小红书
```

Claude 将自动：
- 生成招聘岗位描述
- 创建封面图和详情图
- 编写小红书文案
- 启动自动发布流程

## Links

- **Original Repository**: https://github.com/iOfficeAI/AionUi
- **Skill Path**: https://github.com/iOfficeAI/AionUi/tree/main/skills/xiaohongshu-recruiter

## License

请参考原始仓库的许可证信息。
