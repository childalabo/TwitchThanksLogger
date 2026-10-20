# 対応ソース／ビルド情報について（beta.4）

候補ID: `ttl-common-native-beta4-cand-20261017-01`

## 提供物

- ファイル名: `TwitchThanksLogger-Native-Source-0.1.0-beta.4.zip`
- SHA-256: `305c730f43a6242f701bd06bb15f56166b8d23a406bccbc1373ee5676b650922`
- サイズ: 45161 byte（22エントリ）
- `BUILD-INFO.json` SHA-256: `ff18c0199095b61ac15bee0af0c071b161e8a06c87e1dfa716696bf4042a2d69`

このZIPには、`TwitchThanksLogger-Beta-Setup.exe` に組み込まれた OBS Native プラグイン（GPL-2.0-or-later）に対応するソース、ビルド設定、ビルド情報、ライセンス／通知が含まれます。内容は、ZIP内の `BUILD-INFO.json` に記録したファイルごとのSHA-256で確認できます。

## 出荷した Native DLL

| 項目 | 値 |
|---|---|
| ファイル | `twitchthankslogger-obs.dll`（Setup に埋め込み） |
| SHA-256 | `1c0e6fc714ca099bbcf7824d0e2c02281775ede7c7530077d5bc2dcefa7f1765` |
| サイズ | 96768 byte |
| 世代 | `0.1.0-beta.4-native.1` |

beta.4 の Native DLL は**1つだけ**で、OBS 32.1.x と 32.2.x の両方の環境で同じものを使います。ビルドは1回で、OBS 32.1.2 / Qt 6.8.3 に対して行いました（Release x64、MSVC 19.44.35228.0、CMake 3.31.6、C++20）。OBS 32.2.2 / Qt 6.11.1 に対して別にビルドしたものではありません。

ソースの系譜は、beta.3 で出荷した OBS 32.1.2 向けの強化（hardened）済みソースを基にして、beta.4 の変更差分（`native/obs-plugin/beta4-delta.patch`）を適用したものです。基になったファイルと最終のファイルのハッシュは `BUILD-INFO.json` にあります。

## 現在の開発ツリーとの関係

ZIPの `native/obs-plugin` は、上の DLL に対応するソースです。ZIPの `BUILD-INFO.json` には、非公開の開発リポジトリ内の識別子が記録されていますが、その開発リポジトリはこのリポジトリには含まれません。

## 記録されている不明点（UNKNOWN）

- beta.3 で出荷したバイナリをビルドしたときの Windows SDK のバージョン
- この DLL を、このソースから同一のバイト列で再ビルドできるかどうか

OBS / Qt の SDK は第三者のものでZIPには含まれません。その入力ファイルのSHA-256は `BUILD-INFO.json` に記録しています。

## 主張しないこと

- 再現可能ビルド（reproducible build）が証明されたとは主張しません。
- 決定的な Native 再ビルドが証明されたとは主張しません。
- GPL の法的適合性が証明されたとは主張しません。

## ソースの公開範囲

このリリースで公開するソースは、上の OBS Native プラグインの対応ソースだけです。

- **TwitchThanksLogger 本体のソースは公開していません。**
- このリポジトリの Git タグ（`v0.1.0-beta.4`）は、配布物の案内用のドキュメントを指しており、アプリ本体のソースを含みません。タグからアプリ本体を再現できるとは主張しません。
- GitHub が自動表示する「Source code (zip / tar.gz)」は、このドキュメントのリポジトリのスナップショットで、OBS Native プラグインの対応ソースではありません。

ライセンス文書（`licenses/OBS-GPL-2.0.txt`、`THIRD_PARTY_NOTICES.md`）はZIPに含まれます。配布ZIPには、.NET などの第三者コンポーネントのライセンスと通知も同梱しています。
