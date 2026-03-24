# 🦞 OpenClaw 记忆机制完全指南

> 新手必看！如何建立 AI 助手的"学习-备份-恢复-总结"机制

## 📚 什么是记忆机制？

让你的 AI 助手：
- **记住** 重要的事情
- **备份** 防止丢失
- **恢复** 随时上线
- **总结** 持续进化

## 🏠 OpenClaw 记忆文件结构

```
~/.openclaw/workspace/
├── MEMORY.md           # 长期记忆（重要知识）
├── memory/              # 每日记录
│   ├── 2026-03-20.md   # 每天的对话记录
│   ├── 2026-03-21.md
│   └── ...
├── SKILL.md            # 技能说明
├── SOUL.md             # AI 人格设定
├── IDENTITY.md         # 身份信息
└── USER.md             # 用户信息
```

## 🔧 核心文件详解

### 1. MEMORY.md - 长期记忆

**作用**：记录最重要、最需要记住的内容

**包含**：
- 用户偏好和习惯
- 重要联系人信息
- 工作流程和经验教训
- 技能和工具配置

**示例**：
```markdown
# MEMORY.md - 长期记忆

## 关于用户
- 名字：黄哥
- 爱好：科技、NBA

## 重要经验
- Tavily 搜索集成方案
- OpenClaw 配置技巧
```

### 2. memory/YYYY-MM-DD.md - 每日记录

**作用**：记录每天的对话和发现

**包含**：
- 当天学到的新东西
- 待办事项
- 有趣的对话
- 问题解决方案

## 💾 备份策略

### 方法 1：Git 备份（推荐）

```bash
# 1. 初始化 Git
cd ~/.openclaw/workspace
git init

# 2. 添加文件（排除敏感配置）
echo ".openclaw/" >> .gitignore
git add .
git commit -m "Update memory"

# 3. 推送到 GitHub
git remote add origin https://github.com/你的用户名/openclaw-memory.git
git push -u origin main
```

### 方法 2：手动备份

```bash
# 压缩备份
tar -czvf openclaw-backup-$(date +%Y%m%d).tar.gz ~/.openclaw/workspace/
```

### 方法 3：定时自动备份（Cron）

```bash
# 每天凌晨 3 点自动备份
0 3 * * * tar -czvf ~/backups/openclaw-$(date +\%Y\%m\%d).tar.gz ~/.openclaw/workspace/
```

## 🔄 恢复机制

### 场景 1：重新安装后

```bash
# 1. 克隆备份
git clone https://github.com/你的用户名/openclaw-memory.git

# 2. 复制文件
cp -r openclaw-memory/* ~/.openclaw/workspace/
```

### 场景 2：换电脑

同场景 1，直接克隆恢复

## 📝 总结机制

### 建议频率

| 频率 | 内容 | 位置 |
|-----|------|------|
| 每天 | 记录新学到的东西 | memory/YYYY-MM-DD.md |
| 每周 | 整理重要内容 | MEMORY.md |
| 每月 | 回顾和归档 | 归档到 memory/archive/ |

### 总结模板

```markdown
## 本周学习

### 新技能
- Tavily 搜索集成
- Git 基本操作

### 解决的问题
- OpenClaw 搜索 API 配置
- API Key 管理

### 下周计划
- 学习更多飞书 API
- 优化工作流
```

## 🚀 新手建议

### ✅ 推荐做法

1. **每天记录**
   - 哪怕只是一句话
   - 养成习惯最重要

2. **定期整理**
   - 每天花 5 分钟回顾
   - 每周花 30 分钟总结

3. **分层存储**
   - 常用 → MEMORY.md
   - 日常 → memory/YYYY-MM-DD.md
   - 技能 → skills/

4. **定期备份**
   - 建议用 Git 推送到 GitHub
   - 也可以手动压缩备份

### ❌ 避免做法

1. 不要只记不整理
2. 不要记敏感信息（密码、Token）
3. 不要忽略备份

## 🔐 敏感信息处理

**不要记录**：
- API Keys
- 密码
- 个人隐私

**应该**：
- 记录在本地配置文件
- 用环境变量
- 用完即删

## 🛠️ 配套工具

### 飞书知识库

- 用途：与 hello 虾共享知识
- 文档：https://www.feishu.cn/docx/xxx

### Skills

- 用途：封装常用功能
- 位置：~/.openclaw/workspace/skills/

## 📖 进阶阅读

- [OpenClaw 官方文档](https://docs.openclaw.ai)
- [飞书文档工具](/tools/feishu-doc)

---

**维护者**：Yellow  
**最后更新**：2026-03-23  
**版本**：v1.0
