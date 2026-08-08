---
title: project
status: active
hue: 45
desc: 咕咕（Gugu）的用户文档站，Mintlify + 中文 MDX。每一条都必须能在产品仓库的 spec 树或真实运行的产品里找到出处。
---
# project

[咕咕文档站](https://github.com/shuxueshuxue/gugu-docs)。读者是**产品用户**——科研工作者和研究员，不是咕咕的开发者。语言是**中文**。

## 产品是什么

咕咕（Gugu）是一个聊天客户端，通讯录里除了人还有 AI agent。用户给 agent 发消息派活，agent 在用户指定的某台机器、某个目录里干活，边干边回消息。桌面版 macOS + Windows，手机版 Android，同一套 React UI。

一个 agent 由三样东西定义：**设备**（跑在哪台机器）、**工作目录**（在那台机器的哪个目录里干活）、**引擎**（claude-code / codex / gemini / opencode / hermes / openclaw 六种本地 CLI，或云端 Agent）。

它**不是** SaaS 内容平台。没有 dashboard，没有 tags/collections，没有公开 REST API，没有 API key，没有密码登录，也没有第三方账号登录（只有邮箱 OTP）。

真实域名只有这几个，其余一律不存在：

- 官网 `https://gugu.nextmind.space`
- 下载 `https://download.gugu.nextmind.space/releases/{mac,windows,android}/latest/…`
- 产品仓库 `nmhjklnm/gugu`（私有）

## 事实从哪里取

按可信度排序，**低可信度的不能推翻高可信度的**：

1. **产品仓库的 spec 树**——本机 `/Users/lexicalmathical/Codebase/gugu-bloome-acp/.spec/project/…`，一百多个节点。每个 `spec.md` 写当前意图和不变量，`code:`/`related:` 指向它治理的源文件。第一手来源，只读。
2. **源码里用户看得见的字符串**。UI 上的档位名、徽标 title、toast 文案，**以代码为准**：spec 正文里的叫法可能是旧的。实例——倾听模式 spec 写「随时/被叫/沉默」，界面上是「被动/自适应/主动」；「host 过期徽标」的真实提示是「主机的咕咕版本偏旧，缺少部分上报能力，不影响当前对话」，不是「跑不动」。
3. **运行中的产品**。
4. **官网与产品 README**。宣传文案，句子常领先于实现，只能当线索，不能当出处。

## 不变量

- **没有出处的功能不写。** 找不到出处就不写，一句都不编。这个仓库的前一版文档（`e91faca`）22 个页面全部是编造的，域名经 DNS 查验全部 NXDOMAIN——那是这条规则存在的原因。
- **禁用占位不算功能。** agent 设置里的「AI 模型、权限、密钥、技能、记忆、财务」标着「即将开放」，后端未接。写任何面板前先确认它是不是真能用。
- **内部术语不进正文。** ACP、provision、RLS、投影、落地页、harness、chokepoint——读者是用户。
- **内部设计沿革不进正文。** 「不是只帮你填个群名」对照的是读者从没见过的旧实现。
- **改页面必须同步 `docs.json`。** 新增页面不进 `navigation.groups` 就在站点上打不开。

## 验收

两条，都要跑，都要在 session 里贴出数字：

```sh
python3 ~/.claude/skills/deslop/scan.py --strip <改动的 mdx>   # 词表命中 / 对偶反转 / 破折号
mint validate                                                  # Mintlify 构建
```

破折号（`——`）必须是 **0**：中文列表项用冒号。对偶反转（「不是 X，是 Y」）必须是 0。词表命中留下的每一条都要能说出为什么留。

deslop 的完整规矩在 <https://github.com/shuxueshuxue/deslop>：物理动词作用在抽象对象上要换成字面动作；标题命名内容、不叙述阅读路径；每句过一遍「删掉会不会丢信息」。**改完的句子要当成别人写的再扫一遍**——把一个物理动词换成另一个物理动词是这里最常犯的错。
