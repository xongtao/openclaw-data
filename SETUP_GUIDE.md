# OpenClaw Data GitHub 同步设置指南

## ✅ 已完成设置

1. ✅ 创建了本地目录结构 `/root/data/`
2. ✅ 将 ProteinAE 讨论内容移动到 `/root/data/paper_comment/proteinAe/`
3. ✅ 初始化了本地 git 仓库
4. ✅ 创建了自动同步脚本
5. ✅ 设置了每天凌晨 3 点的定时任务

## 🚀 需要手动完成的步骤

### 步骤 1: 登录 GitHub

在终端运行：

```bash
gh auth login
```

按提示操作：
- 选择 `GitHub.com`
- 选择 `HTTPS`
- 选择 `Y` 通过浏览器登录
- 复制显示的 code 到浏览器授权

### 步骤 2: 首次推送

登录完成后，运行：

```bash
bash /root/.openclaw/workspace/scripts/sync_openclaw_data.sh
```

这会：
- 在 GitHub 上创建 `openclaw-data` 仓库
- 推送所有本地数据到 GitHub

### 步骤 3: 验证

访问 `https://github.com/你的用户名/openclaw-data` 查看是否成功。

## 📁 目录结构规范

以后抓取的数据请按以下结构存放：

```
/root/data/
├── paper_comment/              # 论文评论
│   └── proteinAe/
│       ├── proteinae_discussion_en.md
│       └── proteinae_discussion_cn.md
├── github_repos/               # GitHub 项目信息
├── arxiv_papers/               # arXiv 论文
├── experiments/                # 实验数据
└── README.md
```

每天凌晨 3 点会自动同步到 GitHub。

## 📊 当前数据

已存储的数据：

| 路径 | 描述 | 大小 |
|------|------|------|
| `/root/data/paper_comment/proteinAe/` | ProteinAE 论文讨论 | ~112KB |

## 🔧 手动触发同步

如需立即同步：

```bash
bash /root/.openclaw/workspace/scripts/sync_openclaw_data.sh
```

查看同步日志：

```bash
tail -f /var/log/openclaw-data-sync.log
```

## ❓ 常见问题

### Q: 如何更改仓库名称？
编辑脚本中的 `REPO_NAME` 变量：
```bash
nano /root/.openclaw/workspace/scripts/sync_openclaw_data.sh
```

### Q: 如何更改为私有仓库？
修改 `create_repo_if_not_exists` 函数中的 `--public` 为 `--private`

### Q: 同步频率如何修改？
编辑 crontab：
```bash
crontab -e
```
修改 `0 3 * * *` 为你想要的频率
