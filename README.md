# mihomo-core

AngelaBox Clash 的内核跟踪仓。官方上游是 [MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo)。

本仓库不是官方 mihomo，也不是 [dukangalex/mihomo](https://github.com/dukangalex/mihomo)（后者是崩坏：星穹铁道 API 的 Python 仓库）。

## 身份

| 项目 | 值 |
|------|-----|
| 产品 | AngelaBox Clash |
| 客户端 | [dukangalex/ClashMetaForAndroid](https://github.com/dukangalex/ClashMetaForAndroid) 分支 `dev` |
| 内核分支 | `chain-dev` |
| 跟踪上游 | MetaCubeX/mihomo `Alpha`（Android 另参 `android-real`） |

产品边界与 [AngelaBox](https://github.com/dukangalex/AngelaBox) 一致：跟随官方内核，不替换协议栈；组链用官方 `dialer-proxy` / 出站覆盖层；Fail Closed。

MetaCubeX 许可要求：非官方下游项目名称不得含有 `mihomo`。对外产品名是 **AngelaBox Clash**，本仓库名仅作内部跟踪仓使用。

## 首次导入官方内核

本仓库目前只有说明文件。在本机执行：

```bash
git clone https://github.com/MetaCubeX/mihomo.git mihomo-core-src
cd mihomo-core-src
git checkout Alpha
git remote add angelabox https://github.com/dukangalex/mihomo-core.git
git checkout -B chain-dev
git push -u angelabox chain-dev --force
```

`--force` 仅用于第一次用官方历史替换空仓。之后只允许 `git fetch` + `git merge`。

CMFA 子模块在内核仓就绪后改为：

```
url = https://github.com/dukangalex/mihomo-core
branch = chain-dev
```

在此之前子模块仍可指向 `MetaCubeX/mihomo` 的 `Alpha`，以便客户端可编译。

## 同步

```bash
git fetch upstream
git checkout chain-dev
git merge upstream/Alpha
# 只解决与链式覆盖层相关的冲突
git push origin chain-dev
```

原则见客户端 [docs/MAINTENANCE.md](https://github.com/dukangalex/ClashMetaForAndroid/blob/dev/docs/MAINTENANCE.md)。
