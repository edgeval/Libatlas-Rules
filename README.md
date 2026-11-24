# LibAtlas Rules

English · [简体中文](README.zh-Hans.md)

This repository maintains the rules used by LibAtlas (库谱) to identify Android native libraries, SDKs, components, and intent actions. It also provides online library descriptions, SDK version data, and chart rules. [LibAtlas app](https://github.com/edgeval/Libatlas)

## Rule downloads

In LibAtlas, open **Settings → Rules and network → Cloud rules** to check for rule updates.

Rule release **0.5.2** uses data version `52` and contains **3,199** identification rules. The Android v5 bundle contains `rules.db` and `metadata.json`. LibAtlas reads the database for offline matching and loads descriptions from the `v4` branch. [Release 0.5.2 files](https://github.com/edgeval/Libatlas-Rules/tree/rules-data/releases/52) · [Latest manifest](https://github.com/edgeval/Libatlas-Rules/blob/rules-data/manifest.json)

## Repository layout

| Location | Contents |
| --- | --- |
| `v4` branch | Rule sources, online descriptions, and compatibility outputs. |
| `libraries/<UUID>.json` and `icons/` | The editable source for library identification rules and SVG icons. |
| `sdk-details/` | SDK version and detection data, including Flutter engine mappings. [SDK details guide](sdk-details/README.md) |
| `chart/` | Chart rules, SVG icons, schemas, and tests. [Chart rules guide](chart/README.md) |
| `rules-data` branch | Published Android v5, portable v5, and legacy v4 bundles and their manifests. [Published data](https://github.com/edgeval/Libatlas-Rules/tree/rules-data) |

## Contributing

Submit changes to `v4` through a pull request. For a new or corrected rule, include the exact identifier, the library or SDK name, the developer, and a verifiable source. An official document, a public SDK package, or a reproducible sample can establish where the identifier comes from. For a sample app, include its name and version. When multiple builds share a filename, use a verified distinguishing identifier or identify the common library family.

Edit the sources in `libraries/` and `icons/`. Use SVG for new icons and `import-icon` to add their index entries. See the [v5 rules contract](docs/rules-v5-contract.md) for fields, matching, and validation.

```sh
python3 tools/rules.py check
python3 -m unittest discover -s tests -v
python3 tools/rules.py build --output /tmp/libatlas-rules
```

The compiler uses the Python standard library. Cross-language tests also require Node.js and a JDK. Chart rules have their own preview and stable channels. [Chart contribution guide](chart/README.md) · [Chart rule skill](skills/libchecker-chart-rules/README.md)

## Upstream and license

LibAtlas Rules is derived from LibChecker-Rules. Thanks to its maintainers and contributors. [Upstream repository](https://github.com/LibChecker/LibChecker-Rules) · [Apache License 2.0](LICENSE)
