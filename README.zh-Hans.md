# 库谱规则库 · LibAtlas Rules

[English](README.md) · 简体中文

本仓库维护库谱（LibAtlas）用于识别 Android 原生库、SDK、应用组件和 Intent Action 的规则，也提供在线库说明、SDK 版本数据和图表规则。[库谱应用](https://github.com/edgeval/Libatlas)

## 获取规则

在库谱中打开 **设置 → 规则与网络 → 云端规则**，即可检查规则更新。

规则版本 **0.5.2** 对应数据编号 `52`，包含 **3,199** 条识别规则。Android v5 包包含 `rules.db` 和 `metadata.json`。库谱用数据库离线匹配，在线说明从 `v4` 分支读取。[0.5.2 发布文件](https://github.com/edgeval/Libatlas-Rules/tree/rules-data/releases/52) · [最新发布清单](https://github.com/edgeval/Libatlas-Rules/blob/rules-data/manifest.json)

## 仓库结构

| 位置 | 内容 |
| --- | --- |
| `v4` 分支 | 规则源文件、在线说明和兼容产物。 |
| `libraries/<UUID>.json` 和 `icons/` | 用于编辑库识别规则和 SVG 图标的源文件。 |
| `sdk-details/` | SDK 版本识别数据，包括 Flutter 引擎映射。[SDK 详情说明](sdk-details/README.md) |
| `chart/` | 图表规则、SVG 图标、数据规范和测试。[图表规则说明](chart/README.zh-Hans.md) |
| `rules-data` 分支 | Android v5、通用 v5 和旧版兼容包及其发布清单。[已发布数据](https://github.com/edgeval/Libatlas-Rules/tree/rules-data) |

## 提交规则

欢迎向 `v4` 分支提交 Pull Request。新增或修正规则时，请附上准确的标识、库名或 SDK 名、开发方以及可核验的来源。可用官方文档、公开 SDK 包或可复现样本验证标识出处。如果使用应用样本，请注明应用名称和版本。多个构建共用文件名时，请提供已验证的区分标识，或标注能够确认的共同库家族。

请在 `libraries/` 和 `icons/` 中修改源文件。新增图标使用 SVG 格式，可以用 `import-icon` 追加索引。字段、匹配方式和验证要求见 [v5 规则规范](docs/rules-v5-contract.md)。

```sh
python3 tools/rules.py check
python3 -m unittest discover -s tests -v
python3 tools/rules.py build --output /tmp/libatlas-rules
```

编译器使用 Python 标准库，跨语言测试还需要 Node.js 和 JDK。图表规则有独立的预览渠道和稳定渠道。[图表贡献指南](chart/README.zh-Hans.md) · [图表规则 Skill](skills/libchecker-chart-rules/README.zh-Hans.md)

## 上游与许可证

库谱规则库派生自 LibChecker-Rules。感谢上游维护者与贡献者。[上游仓库](https://github.com/LibChecker/LibChecker-Rules) · [Apache License 2.0](LICENSE)
