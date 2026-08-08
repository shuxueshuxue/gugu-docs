# 给写这份文档的 agent

## 产品是什么

咕咕（Gugu）是一个聊天客户端，通讯录里除了人还有 AI agent。用户给 agent 发消息派活，agent 在用户指定的某台机器、某个目录里干活，边干边回消息。桌面版 macOS + Windows，手机版 Android。

它**不是** SaaS 内容平台，没有 dashboard，没有 tags/collections，没有公开 REST API，没有 API key，没有密码登录，也没有第三方账号登录。

已知真实的域名只有这几个：

- 官网 `https://gugu.nextmind.space`
- 下载 `https://download.gugu.nextmind.space/releases/{mac,windows,android}/latest/...`
- 产品仓库 `nmhjklnm/gugu`（私有）

`gugu.app` 及其任何子域都不是咕咕的域名。写进文档前先解析一遍。

## 事实从哪里取

按可信度排序：

1. **产品仓库的 spec 树**（`.spec/project/...`，一百多个节点）。每个节点的 `spec.md` 写的是当前意图和不变量，`code:`/`related:` 指向它治理的源文件。这是第一手来源。
2. **源码里用户看得见的字符串**。UI 上的档位名、徽标提示、toast 文案，以代码为准——spec 正文里的叫法可能是旧的。写倾听模式时 spec 说「随时/被叫/沉默」，界面上其实是「被动/自适应/主动」。
3. **运行中的产品**。截图、实际点一遍。
4. **官网和 README**。它们是宣传文案，句子可能领先于实现，只能当线索，不能当出处。

## 不能写的东西

- **没有出处的功能。** 找不到出处就不写。一句都不要编。
- **禁用占位当成功能。** agent 设置里的「AI 模型、权限、密钥、技能、记忆、财务」标着「即将开放」，后端没接。类似的占位随时会有新的，写之前确认那个面板是不是真的能用。
- **内部术语。** 读者是科研工作者，不是咕咕的开发者。ACP、provision、RLS、投影、落地页、harness 这些不要出现在正文里。
- **内部设计沿革。** 「不是只帮你填个群名」这种对照的是一个读者从没见过的旧实现，删掉。

## 文风

用 [deslop](https://github.com/shuxueshuxue/deslop) 审。写完跑：

```sh
python3 ~/.claude/skills/deslop/scan.py --strip *.mdx
```

三个数：词表命中、对偶反转、破折号。当前基线是 4 / 0 / 0，破折号必须是 0——中文列表项用冒号，不用 `——`。

其余按 deslop 的规矩：物理动词作用在抽象对象上要换成字面动作；标题命名内容，不叙述阅读路径；每句过一遍「删掉会不会丢信息」。

## Mintlify

页面是带 YAML frontmatter 的 MDX，导航在 `docs.json`。新增页面要同时加进 `docs.json` 的 `navigation.groups`，否则站点上打不开。本地预览 `mint dev`。
