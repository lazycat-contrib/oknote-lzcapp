# oknote-lzcapp

[OKNote](https://oknote.top) 的 LazyCat LPK 打包 —— 自托管笔记应用（单容器）。

## 形态

- 单容器镜像：`wanpidadajuan/oknote`，端口 38080
- 镜像交付：mirror 模式（`docker.1ms.run/wanpidadajuan/oknote:{tag}`），digest 校验开启
- 版本发现：Docker Hub 纯 SemVer tag（`^[0-9]+[.][0-9]+[.][0-9]+$`），排除 `-amd64` / `-arm64` 变体与 `latest` / `dev`
- 数据持久化：
  - `/lzcapp/var/data` → `/app/data`
  - `/lzcapp/var/config` → `/app/config`

## 结构

- `package.yml` — LPK v2 包元数据（`community.lazycat.app.oknote`）
- `lzc-manifest.yml` — 单服务 + upstreams + 双卷持久化
- `.github/lazycat-action.yml` — 镜像版本源，mirror 交付，仅私有商店
- `.github/workflows/lazycat.yml` — 每日自动跟版 + 发布喵喵商店
