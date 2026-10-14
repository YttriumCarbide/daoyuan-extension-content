# 道渊状态栏扩展与广告

此仓库管理状态栏“扩展”弹窗中的两个内容栏位：

- `extensions.json`：扩展。
- `ads.json`：广告。

投票仍由 Cloudflare 投票服务管理，不在这里保存账号、选票或密钥。

## 添加内容

点击对应 JSON 文件右上角的铅笔按钮，修改 `items` 数组并提交。每条内容使用以下格式：

```json
{
  "id": "example-entry",
  "title": "这里填写标题",
  "description": "这里填写介绍。支持换行文本，不支持 HTML。",
  "imageUrl": "https://你的图床/图片.png"
}
```

- `id`：条目的固定标识，同一文件内不能重复。
- `title`：标题，最多 120 字。
- `description`：介绍，最多 5000 字，换行写为 `\n`。
- `imageUrl`：HTTPS 图片直链；没有图片时填写空字符串。请填图片本身的 URL，不要填图床预览页面。
- 数组中的顺序就是状态栏的显示顺序。删除数组中的条目即可下架。
- 编辑后更新 `updatedAt`。保留 `schemaVersion: 1`。
- `items: []` 表示暂时没有内容，不要把示例当作真实广告发布。

完整示例：

```json
{
  "schemaVersion": 1,
  "updatedAt": "2026-10-15",
  "items": [
    {
      "id": "my-extension",
      "title": "我的扩展",
      "description": "第一行介绍\n第二行介绍",
      "imageUrl": "https://你的图床/图片.png"
    }
  ]
}
```

## 状态栏读取地址

- 扩展：`https://raw.githubusercontent.com/YttriumCarbide/daoyuan-extension-content/main/extensions.json`
- 广告：`https://raw.githubusercontent.com/YttriumCarbide/daoyuan-extension-content/main/ads.json`

仓库需要保持公开，普通玩家才能直接读取。状态栏打开相应栏位时加载，并短时缓存；GitHub/CDN 的缓存可能使刚提交的内容稍后才出现。不要在文件里写入私人信息、账号令牌或 API Key。
