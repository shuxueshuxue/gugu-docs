---
scenarios:
  - name: settings-page
    description: >
      在桌面浏览器中从文档站导航进入“设置与账号”，检查页面渲染及关键说明。
    expected: >
      导航可以进入 /settings；页面显示账户资料与咕咕号、模型、额度与充值、通知、
      版本与更新五个部分；模型部分明确区分咕咕服务器提供的模型与本地 agent 的 CLI 配置；
      通知部分列出新消息、agent 开始工作或上线、启动失败和回复失败。
    tags: [frontend-e2e, desktop]
---

通过本地 Mintlify 预览和桌面浏览器执行。使用浏览器看到的导航与页面正文判断结果，不以读取 MDX 源文件代替。
