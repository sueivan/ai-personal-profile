# 待办跟踪：Issues 模板与本地同步

本文件包含两部分：
1. **建议创建的 GitHub Issues**（复制标题/正文到仓库 Issues 页面一键新建）
2. **本地初始化与同步脚本**（仓库建好后如何 commit + push）

---

## 一、建议创建的 Issues（待办跟踪）

把下面每条作为独立 Issue 提交，方便逐步填充档案。

### Issue 1 · 补充教育履历
**标题**：`[档案] 补充"个人简介与背景"中的教育履历`
**正文**：
```
章节：1. 个人简介与背景
任务：补全学历、学位授予单位、关键任职时间线。
验收：README 该章节不再含"示例补充位"占位。
标签：documentation
```

### Issue 2 · 完善技术栈版本号
**标题**：`[档案] 完善"常用工具与技术栈"版本号`
**正文**：
```
章节：4. 常用工具与技术栈
任务：核对 R / Python / Zotero 插件等当前版本，避免示例过期。
标签：chore
```

### Issue 3 · 项目成果补链接
**标题**：`[档案] 为"项目经验与成果"补充对外链接`
**正文**：
```
章节：5. 项目经验与成果
任务：为各代表项目补充 DOI / 仓库 / 公众号链接。
标签：enhancement
```

### Issue 4 · 季度复盘长期目标
**标题**：`[档案] 季度复盘并更新"长期目标"`
**正文**：
```
章节：6. 长期目标
任务：每季度回顾一次，标记已完成项、新增方向。
标签：review
```

---

## 二、本地初始化与同步脚本

> 前提：GitHub 仓库已存在（`https://github.com/sueivan/ai-personal-profile`）。
> 若使用 `gh` CLI 且已登录，可直接用脚本自动建仓+推送；否则先在网页点 "New repository" 建好公开仓库，再跑推送部分。

### 方式 A：已安装并登录 `gh`（推荐，一条命令建仓+推送）

```powershell
# PowerShell（Windows）
cd ai-personal-profile
git init -b main
git add README.md issues.md
git commit -m "init: 跨 AI 共享个人档案骨架"
gh repo create ai-personal-profile --public --description "跨 AI 共享个人档案" --source . --remote origin --push
```

### 方式 B：仓库已在网页建好，仅推送

```powershell
# PowerShell（Windows）
cd ai-personal-profile
git init -b main
git add README.md issues.md
git commit -m "init: 跨 AI 共享个人档案骨架"
git remote add origin https://github.com/sueivan/ai-personal-profile.git
git branch -M main
git push -u origin main
```

### 日常更新（可追溯 / 可回退）

```bash
git add -p            # 选择性暂存
git commit -m "docs: 更新长期目标章节"
git push
# 查看历史
git log --oneline
# 回退单个文件到某次提交
git checkout <commit-hash> -- README.md
```

---

## 三、开启 Issues / Projects 跟踪

- **Issues**：仓库默认开启。进入 `Settings → General` 确认 "Issues" 勾选即可。
- **Projects（看板）**：进入仓库 `Projects` 标签 → `New project` → 选 "Board" 视图，把上述 Issue 拖入 "Todo / In Progress / Done"。
