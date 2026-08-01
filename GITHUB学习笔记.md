# GitHub 学习笔记

> 本仓库用于练习 GitHub Flow。这份笔记记录了我在初学 GitHub 时梳理的核心概念与常用操作，作为自己的学习存档。

---

## 一、GitHub 是什么

**GitHub = 代码版的「网盘 + 朋友圈 + 协作工具」**。

- **Git**：版本控制工具，记录每次修改、可随时回到历史版本（类似文档的「历史版本」）。
- **Hub**：把 Git 放到网上，让大家能一起看、一起改。

三个核心用途：
1. **备份 / 托管代码**：代码不丢，换电脑也能拉下来。
2. **开源分享**：别人能看、能下载、能帮你改。
3. **团队协作**：多人同时开发一个项目不打架。

---

## 二、核心概念（用「写书」打比方）

| 概念 | 大白话 | 比喻 |
|------|--------|------|
| **Repository（仓库 / repo）** | 一个项目的文件夹 | 一本书 |
| **Commit（提交）** | 一次有记录的修改 | 在书稿上做了一段修改并标注「改了第3章」 |
| **Branch（分支）** | 从主线分出来的平行版本，互不干扰 | 复印一本草稿自己乱画，画完再合并回正本 |
| **Clone（克隆）** | 把仓库下载到自己电脑 | 把书复印带回家 |
| **Fork（分叉）** | 把别人的仓库复制到自己账号下 | 借别人的书，印一本归自己 |
| **Pull Request（PR，拉取请求）** | 请求把你的修改合并回原项目 | 你改好了，请原作者「把我的修订收进正本」 |
| **Issue（议题）** | 讨论 bug、提建议的地方 | 在书后面写便条提意见 |
| **Star（星标）** | 收藏 + 点赞 | 喜欢这本书，加个书签 |
| **README** | 项目说明文档，打开仓库第一眼看到 | 书的封面简介 |

---

## 三、实际场景用法

### 1. 下载 / 用别人的代码
- 打开别人仓库 → 点绿色 **Code** 按钮 → **Download ZIP**（直接下载）或用 `git clone` 拉到本地。
- 想收藏就点右上角 **Star**。

### 2. 管理自己的项目（日常三板斧）
```bash
git add .              # 把改动放进「暂存区」
git commit -m "说明"   # 提交一次修改（写清楚改了啥）
git push               # 推送到 GitHub
```

### 3. 别人帮你改（PR 流程）
别人 **Fork → 改 → 提 PR → 你在 Pull requests 里看 → 合并（Merge）**。

---

## 四、首次把本地项目推到 GitHub 的完整流程

1. **本地初始化仓库**
   ```bash
   git init
   git add .
   git commit -m "首次提交"
   ```
2. **GitHub 网页新建仓库**（不要勾选 Add README / Add .gitignore，避免和本地冲突）。
3. **关联远程并推送**
   ```bash
   git remote add origin https://github.com/用户名/仓库名.git
   git branch -M main
   git push -u origin main
   ```
4. **认证**：Windows 上一般用 Git Credential Manager，推送时弹出浏览器，点「授权 git-ecosystem」即可，之后会记住凭证。

---

## 五、常见 Git 命令速查

```bash
git clone <仓库地址>        # 克隆远程仓库到本地
git status                 # 查看当前改动状态
git add .                  # 添加所有改动到暂存区
git commit -m "说明"        # 提交
git push                   # 推送到远程
git pull                   # 拉取远程最新（别人改了就先 pull 再 push）
git branch                 # 查看分支
git checkout -b 新分支名    # 新建并切换到分支
git log --oneline          # 查看提交历史
```

---

## 六、协作进阶：Fork + PR 给别人贡献代码

1. 在别人仓库点 **Fork**，复制到自己的账号下。
2. `git clone` 自己的 Fork 到本地。
3. `git remote add upstream 原仓库地址`（方便同步原项目更新）。
4. 新建分支 `git checkout -b fix-xxx`。
5. 改完 `git add .` → `git commit` → `git push origin fix-xxx`。
6. 回原仓库点 **New pull request**，选择「从你的分支 → main」，写清楚改了什么、为什么。

---

## 七、新手避坑建议

1. **Commit message 写清楚**：别写「改了点东西」，写「修复打卡后定位不显示」。
2. **公开仓库不要提交密码 / Key**：地图 Key、云环境 ID、Token 等要脱敏（换成占位符）。
3. **先网页熟悉，再学命令行**：网页能完成建仓库、改文件、提 Issue。
4. **善用 README 和 CONTRIBUTING**：README 是项目门面，CONTRIBUTING 是协作说明书。
5. **遇到报错别慌**：报错提示通常明确，复制出来搜一下基本有答案。

---

## 八、实战例子

我另一个仓库 `badminton-checkin`（羽毛球打卡小程序）就是按上面的流程开源的：
- 本地 `git init` → 脱敏敏感信息 → 提交。
- GitHub 新建仓库 → 关联远程 → 推送。
- 加了 `README.md` 和 `CONTRIBUTING.md`，方便别人使用和协作。

> 记录于 2026-08，初学 GitHub 的练习存档。
