# TwitchThanksLogger

TwitchThanksLogger は、Twitch配信者・VTuber向けの Windows / OBS 用ツールです。配信中に発生した「お礼の対象」をローカルに記録し、配信後に日本語のお礼文を準備しやすくします。

> **現在は Limited Public Beta（限定的な公開ベータ）です。** 正式版（一般提供）ではありません。ダウンロードは [GitHub Releases](https://github.com/childalabo/TwitchThanksLogger/releases) から入手できます。

## できること

- 配信中のお礼対象をローカルに記録します。
- 配信後に、日本語のお礼文の作成を補助します。
- 次の6種類のイベントを対象にしています。
  - Follow
  - New Sub
  - Resub
  - Gift
  - Cheer
  - Watch streak
- Twitch公式の API / EventSub のみを使用します。スクレイピングや非公開APIは使用しません。

## 対応環境

想定環境: Windows 11 x64

動作確認の対象として限定的に確認した OBS の組み合わせは次の2つです。

- OBS 32.1.2 / Qt 6.8.3 / x64
- OBS 32.2.2 / Qt 6.11.1 / x64

最終的な実行時の確認は、次の環境で行いました。

- Windows 11 Home build 26300 x64
- OBS 32.2.2
- Qt 6.11.1

上記以外のすべての Windows 11 ビルドや、すべての OBS 32.x バージョンで動作確認したわけではありません。

## 使い方

基本的な流れは次のとおりです。

1. TwitchThanksLogger をインストールし、OBS と連携させます。
2. Twitch アカウントで認証（OAuth）します。
3. 配信中、対象イベントがローカルに記録されます。
4. 配信後に記録を確認し、お礼文を作成します。作成した文面は Windows のクリップボードに書き込まれます。

## データとプライバシー

- 記録は、お使いの PC 上のローカル SQLite に保存されます。
- Twitch の OAuth 認証情報は、Windows DPAPI で保護してローカルに保存されます。
- アプリと OBS 連携部分との通信は、ローカルのループバック通信で行われます。
- 一般的なテレメトリー（利用状況の自動送信）は行いません。
- Twitch や配信に由来して保存される履歴は、**24時間**で削除する **製品の方針** としています。これは Twitch の要件ではありません。
  - アプリや PC が停止したまま保持期間を過ぎた場合、期間を過ぎた履歴は、次回の通常のアプリ起動時に削除されます。
  - 停止中に、ちょうど24時間で削除されることは約束しません。
- 完成したお礼文そのものは、TwitchThanksLogger では保存しません。
- 作成した文面は Windows のクリップボードに書き込まれます。Windows のクリップボード履歴は TwitchThanksLogger の管理外であり、アプリから削除することはできません。

## Limited Public Betaについて

これは **LIMITED PUBLIC BETA** です。記録の取りこぼし、OBS連携の不具合、その他の不具合が発生する可能性があります。大規模な配信での信頼性や、あらゆる条件での長時間安定動作は保証しません。

実際の Twitch での確認範囲は次のとおりです。

- 確認済み: OAuth 認証、保存済み認証情報での再起動、通常の実配信（オンライン / オフライン / 配信後処理）、自然に発生した Follow 1件。
- 実配信で自然には最後まで確認できていない: Sub、Resub、Gift、Cheer、Watch streak。

## ダウンロード

Limited Public Beta は GitHub Releases で配布しています。

配布物（Setup.exe、TwitchThanksLogger-Logger.zip、OBS Nativeプラグインの対応ソース／ビルド情報ZIP、SHA-256一覧）は [GitHub Releases](https://github.com/childalabo/TwitchThanksLogger/releases) にあります。実行前に必ずSHA-256を照合してください。

## 不具合報告

不具合報告の公式の窓口は GitHub Issues です。

- [GitHub Issues](https://github.com/childalabo/TwitchThanksLogger/issues)

このベータ版では、匿名での不具合レポート送信機能は利用できません。

## ソースコードについて

TwitchThanksLogger本体のソースコードは、現在公開していません。将来的なオープンソース化は検討していますが、現時点で予定や時期は確定していません。OBS Nativeプラグインについては、配布版に対応するソースおよびビルド情報をReleaseとあわせて提供します。

## ライセンス

TwitchThanksLogger 全体に適用されるライセンスは、現時点では設定していません。このリポジトリは、プロジェクト全体がオープンソースであることを示すものではありません。

OBS Nativeプラグインには GPL-2.0-or-later の対象となるコードが含まれています。この部分に対応するソースおよびビルド情報は、該当する配布版とあわせて別途提供します。
