# YouTube (Music) Enhance — Quantumult X

Quantumult X 原生重写版本，基于 [Maasea/sgmodule](https://github.com/Maasea/sgmodule) 的 YouTube Enhance 脚本适配。

## 功能

- YouTube / YouTube Music 广告请求过滤
- 播放器响应中的画中画（PiP）和后台播放能力增强
- 首页、搜索、队列等响应中的广告内容过滤
- Quantumult X 的 `script-response-body` / `script-request-body` 格式
- 保留上游脚本的跨客户端适配器：脚本会根据运行环境识别 Quantumult X、Surge 或 Loon

## 文件

- `YouTube.Enhance.conf`：Quantumult X 重写配置
- `youtube.response.js`：Maasea 上游响应处理脚本
- `youtube.request.js`：Maasea 上游请求处理脚本

## 导入

在 Quantumult X 的 `[rewrite_remote]` 中添加：

```ini
https://raw.githubusercontent.com/25175/quantumultx-youtube-music-enhance/main/YouTube.Enhance.conf, tag=YouTube Music Enhance（QX）, update-interval=86400, opt-parser=false, enabled=true
```

本仓库只存放公开的 YouTube 重写资源，不存放任何个人 QX/Surge 完整配置、机场订阅、节点密码或证书。按 Surge 分组和订阅结构生成的本机私有 QX 配置位于用户的 Downloads 目录，不应上传到 GitHub。

也可以直接将 `YouTube.Enhance.conf` 内容放入本地 `[rewrite_local]`，并把脚本文件保存到 Quantumult X 的脚本目录后，改为本地脚本路径。

## 重要说明

1. 不要同时启用本项目与以下 YouTube 响应体重写：
   - ddgksf2013 `YoutubeAds.conf`
   - Maasea `YouTube.Enhance.sgmodule`
   - ZenmoFeiShi `Youtube.snippet`
   - app2smile `youtube-qx.conf`
   - 其他匹配 `youtubei.googleapis.com` 并使用 `script-response-body` 的规则
2. 配置文件必须启用 Quantumult X MITM，并安装、信任 QX 证书。
3. YouTube Music 的后台播放和画中画仍受 YouTube 客户端、账号、地区、服务端版本影响；本项目不伪造或修改订阅/支付状态。
4. 如果锁屏封面或当前歌曲媒体信息异常，先禁用所有其他 YouTube 重写，只单独测试本项目。若仍异常，说明问题不一定来自代理重写。
5. 不适用于允许 UDP 转发的 YouTube 流量场景；若广告仍出现，可针对 `googlevideo.com` 的 UDP 443 做单独诊断，不建议一开始扩大到全局 UDP 丢弃。

## 来源与许可

本项目只重新组织 Quantumult X 配置格式，脚本主体来源于 Maasea/sgmodule。请遵守上游项目许可证、YouTube 服务条款及当地法律。该项目不保证对所有 YouTube/YouTube Music 版本有效。
