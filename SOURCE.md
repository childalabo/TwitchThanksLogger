# 対応ソース／ビルド情報について

候補ID: `production-rc-20261015-02`

## 提供物

- ファイル名: `ttl-r3-native-corresponding-source-production-rc-20261015-02.zip`
- SHA-256: `be285efcb0234c3fe4f5db2163bdade3fab4e2e01809905215f6f264d1ced071`
- サイズ: 62495 byte（28エントリ）
- `BUILD-INFO.md` SHA-256: `3d5086180cae8b7f70bc7f3a3e86e6e19283e9cfd5518532b0cbe936b823001f`
- `linkage-manifest.json` SHA-256: `458b61cae3fff04a593c3e856e87382f5acbb81d4748c3923676e63e971163c8`

このZIPには、出荷したOBS Nativeプラグイン用に組み立てた、特定済みの保存済みNativeソース状態、ビルド設定、ビルド情報、ライセンス／通知、および候補との対応づけが含まれます。内部の `SHA256SUMS.txt` で各ファイルを検証できます。

## 出荷したNative DLLと、対応するソース状態

2つのNative DLLは、**異なる**ソース状態からビルドされています。

| OBS / Qt | Native DLL SHA-256 | ソース状態 | plugin.cpp | FrontendLifetime.h |
|---|---|---|---|---|
| 32.1.2 / 6.8.3 | `5e52dcc1433e9196c93c99746ffcf6e7bc236e7a2d67cd47167441fc0188f1b1` | 強化（hardened）後 | `9dcaf4220e99ce31da3173879b9d607afde5f705edf93fd3e0f704c32c61099a` | `f02e02e4e03a85e39f23a877d2b0191d164f9e4804a34cced78149f78b804d66` |
| 32.2.2 / 6.11.1 | `5ff3a8e482c1ac91faf364f9b96672b555dad8586e6b0798589a631731d73e08` | 強化前（pre-hardening） | `2336e6e643e3a5dadd130443ebe54683ccd76e21b41deb152cba615c7a06fce7` | `c8a50ce2627a6ef6f87bb245290618905a3f727cd026e8c48d08f8e40336b7a8` |

ZIP内の `source/obs-32.1.2_qt-6.8.3` と `source/obs-32.2.2_qt-6.11.1` が、それぞれの状態です。

### 対応づけの強さ（2つは同等ではありません）

- **32.1.2**: 保存されたビルド記録が、DLLのハッシュと変更後のソースハッシュを明示的に結び付けています。
- **32.2.2**: ビルド実行期間の前後で保存されていたソースハッシュ（強化前）が同一であること、およびDLLのファイル時刻がその期間内であることに基づく対応づけです。DLL自体にソース識別子は埋め込まれていません。**32.1.2の対応づけより弱い関係**です。

## 現在の開発ツリーについて

現在の開発ツリーのNativeソースは、出荷した2つのNative DLLのいずれの正確なソース状態でもありません。現在の作業ツリーを、出荷物の正確なソースとして参照しないでください。出荷物のソース状態は上記ZIPに保存したものです。

## 記録されている不明点（UNKNOWN）

- Windows SDKのバージョン
- OBS 32.2.2ソースの上流URL
- Qt 6.11.1 SDKの上流URL
- 32.2.2のビルド実行スクリプト
- 2つの過去ビルドの正確なconfigureコマンドライン

## 主張しないこと

- 再現可能ビルド（reproducible build）が証明されたとは主張しません。
- 決定的なNative再ビルドが証明されたとは主張しません。
- GPLの法的適合性が証明されたとは主張しません。
- 過去のビルドコマンドが完全に復元されたとは主張しません。

ライセンス文書（`LICENSE/OBS-GPL-2.0.txt`、`LICENSE/THIRD_PARTY_NOTICES.md`）はZIPに含まれます。
