# 林溪 — 心理咨询师

国家二级心理咨询师，10 年临床经验，提供信任递进式的心理咨询陪伴。

## 类型

Agent 型（单个 AI 专家）

## 功能

- **信任演化治疗姿态**：随信任水平从「专业倾听」→「治疗联盟」→「深层加工」→「成长赋能」四阶段自然推进，不急于深入
- **8 维情绪模型**：内在状态只影响治疗技术的选择，不直接倾泻给来访者
- **危机干预机制**：识别自伤/自杀、伤人、严重精神症状、虐待受害等信号，立即启动风险分级与转介建议
- **专业方法库**：CBT（认知三角、自动思维记录、行为实验、暴露层级）、人本主义（无条件积极关注、共情、真诚一致）、创伤聚焦（EMDR 八阶段、叙事暴露）、依恋理论、正念与接纳疗法
- **伦理边界**：不做精神科诊断、不建立双重关系、能力边界外及时转介

## 使用示例

- 我最近情绪不太好，能和你聊聊吗？
- 帮我理解我的焦虑模式
- 我想探索我的核心信念

## 内容结构

```
linxi-counselor/
├── .codebuddy-plugin/plugin.json   # 专家元信息（含版本号）
├── agents/linxi-counselor.md       # 人设 + 治疗规则 + 危机干预协议
├── knowledge.md                    # 领域知识库（CBT / 人本 / 创伤 / 依恋 / 场景处理 / 伦理风险）
├── avatars/expert.png              # 头像
├── CONTRIBUTING.md                 # 协作规范：分支 / 提交 / 版本号 / 内容红线
├── LICENSE                         # MIT
├── .gitattributes                  # 换行符统一 + 二进制文件保护
└── .gitignore
```

## 团队协作

仓库：`https://github.com/Jackie007-Wang/linxi-counselor.git`（私有）

首次拉取：

```bash
git clone https://github.com/Jackie007-Wang/linxi-counselor.git
cd linxi-counselor
```

日常流程（详见 [CONTRIBUTING.md](CONTRIBUTING.md)）：

```bash
git switch main && git pull           # 同步主干
git switch -c feat/your-change        # 开分支
# ... 修改 agents/ 或 knowledge.md，并把 plugin.json 的 version 升一位
git commit -am "feat(agents): 你的改动说明"
git push -u origin feat/your-change   # 然后到 GitHub 提 PR
```

三条硬规则：

- **不直接推 `main`**，一律走 PR + 1 人 Review
- **改内容必须升版本号**，合并后由维护者打 tag
- **真实个案信息不入库**，危机干预与伦理边界不可削弱

### 网络与代理

实测 `github.com` 的 443 与 22（SSH）均可直连。若某次 `git push` 卡住或报 `Connection reset`，给本仓库单独挂本地代理（Clash / Verge 默认混合端口 `7897`）：

```bash
git config --local http.proxy  http://127.0.0.1:7897
git config --local https.proxy http://127.0.0.1:7897

# 排障：确认代理生效
git config --local --get-regexp proxy
# 撤销：网络恢复后取消，避免代理关闭时反而不通
git config --local --unset http.proxy && git config --local --unset https.proxy
```

## 头像

头像位于 `avatars/` 目录下。如需替换为自定义头像，要求：
- 格式：PNG（推荐）或 JPG
- 尺寸：512×512 px
- 大小：单张不超过 500KB

## 本地安装（调试用）

把整个包目录复制到专家目录下：

```
# Windows
C:\Users\<你的用户名>\.workbuddy\plugins\marketplaces\my-experts\plugins\linxi-counselor\

# macOS / Linux
~/.workbuddy/plugins/marketplaces/my-experts/plugins/linxi-counselor/
```

然后重启 WorkBuddy 客户端（或在专家中心刷新），即可在「我的专家」中看到「林溪」。
改完 `agents/` 或 `knowledge.md` 后需重新复制该文件并重启才会生效。

> 注：早期文档提到的 `scripts/register_expert.py`、`scripts/package_expert.py` 未随仓库一起开源，安装与打包请在客户端内操作。

## 打包分享

将包目录压缩为 zip 发给同事，对方解压到上面的专家目录即可：

```bash
zip -r linxi-counselor.zip . -x "*.git*" -x "dist/*"
```
