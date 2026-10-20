# TwitchThanksLogger

TwitchThanksLogger は、Twitch配信者・VTuber向けの Windows / OBS 用ツールです。配信中に発生した「お礼の対象」をローカルに記録し、配信後に日本語のお礼文を準備しやすくします。

現在のバージョン: **0.1.0-beta.4**

> **現在は Limited Public Beta（限定的な公開ベータ）です。** 正式版（一般提供）ではありません。ダウンロードは [GitHub Releases](https://github.com/childalabo/TwitchThanksLogger/releases) から入手できます。

## できること

- 配信中のお礼対象をローカルに記録します。
- 配信後に、日本語のお礼文の作成を補助します。お礼の最後の言葉や、連続視聴の注記は、設定で変更・表示／非表示にできます。
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

OBS の対応状況は次のとおりです（Windows x64）。

| 環境 | 状態 |
|---|---|
| OBS 32.1.2 / Qt 6.8.3（通常インストール版） | 対応確認済み |
| OBS 32.2.2 / Qt 6.11.1 | ポータブル環境で動作確認済み。通常インストール版は正式には未確認 |
| その他の 32.1.x（Qt 6.8.x）・32.2.x（Qt 6.11.x） | 正式には未確認。Setupの互換性チェックに合格した場合に限り、確認画面で承知のうえ続行できます |
| 上記以外（32.0以前、32.3以降、33系など） | 対応していません |

「対応確認済み」は、その環境での限定的な確認を意味します。長時間配信での安定性や、すべての OBS 32.x への対応を意味するものではありません。上記以外のすべての Windows 11 ビルドで動作確認したわけではありません。

## インストールと使い方

1. [GitHub Releases](https://github.com/childalabo/TwitchThanksLogger/releases) から `TwitchThanksLogger-Beta-Setup.exe` をダウンロードし、実行する前にSHA-256を照合します（下記「ダウンロード」）。OBS と TwitchThanksLogger を終了してから実行します。
2. Setup の案内に沿って、本体のインストール、Twitch へのログイン（配信者本人のアカウントで許可）、OBS 連携の追加を進めます。Setup は OBS を導入しません。OBS を先にインストールしておいてください。
3. 次回からは OBS を開くだけで使えます。配信中、対象イベントがローカルに記録されます。
4. 配信後に記録を確認し、お礼文を作成します。作成した文面は Windows のクリップボードに書き込まれます。

すでにインストール済みの状態で Setup を開くと、「修復」と「削除」を選べる画面が表示されます。削除は確認のうえで行われ、既定は「キャンセル」です。更新・修復・削除に Twitch へのログインは必要ありません。

### 未署名のBetaについて

この Beta は**未署名**です。Windows の Microsoft Defender SmartScreen が「Windows によって PC が保護されました」と表示することがあります。未署名のためで、この警告は解消されていません。ダウンロードしたファイルのSHA-256を、公開されている値と照合してください。実行する場合は「詳細情報」→「実行」を選びます。Windows のセキュリティ機能を無効にする必要はありません。

### beta.3 からの更新について

beta.3 から beta.4 への更新は、隔離した実 Windows 環境で、通常の更新経路（実際に配布された beta.3 の上で beta.4 の Setup を実行）、設定の保持、起動を確認しています。beta.4 は限定的な公開ベータであり、すべての Windows / OBS 環境での動作を保証するものではありません。更新の前後は OBS と TwitchThanksLogger を閉じてください。

問題が起きた場合は、表示に従って Setup を開き直してください。解決しない場合は、Windows の「設定」→「アプリ」から正式にアンインストールしたあと、新しい Setup を試してください。この手順は、実機では広く確認していません。

## 新しいBetaのお知らせ（任意）

- 設定でONにした場合だけ、公式のリリース情報（このリポジトリの GitHub Releases）を確認します。**既定はOFFです。**
- 新しい版があれば知らせます。通知を押すと、公式の版のリリースページが開きます。ダウンロードと実行は自分で行います。自動でダウンロード・インストール・更新はしません。

## データとプライバシー

- 記録は、お使いの PC 上のローカル SQLite に保存されます。
- Twitch の OAuth 認証情報は、Windows DPAPI で保護してローカルに保存されます。
- アプリと OBS 連携部分との通信は、ローカルのループバック通信で行われます。
- 利用状況の収集（テレメトリー・分析）や、識別子の送信は行いません。追加の情報収集もありません。Twitch の認証・API / EventSub との通常の通信と、上の任意の更新確認は、テレメトリーではありません。
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

| ファイル | 内容 |
|---|---|
| `TwitchThanksLogger-Beta-Setup.exe` | セットアップ |
| `TwitchThanksLogger-Beta-0.1.0-beta.4-win-x64.zip` | 配布ZIP |
| `TwitchThanksLogger-Native-Source-0.1.0-beta.4.zip` | OBS Nativeプラグインの対応ソース／ビルド情報 |
| `SHA256SUMS.txt` | 上の3つのSHA-256一覧 |

実行前に、PowerShell で次を実行し、`SHA256SUMS.txt` の同名ファイルの値と一致することを確認してください。

```powershell
Get-FileHash .\TwitchThanksLogger-Beta-Setup.exe -Algorithm SHA256
```

ハッシュはファイルが一致することを確認するもので、発行元を保証するものではありません。

## 不具合報告

不具合報告の公式の窓口は GitHub Issues です。

- [GitHub Issues](https://github.com/childalabo/TwitchThanksLogger/issues)

このベータ版では、不具合レポートの送信先を設定していないため、**送信機能は使えません**。自動で送信されることもありません。設定の「診断ZIPを作成」で作ったファイルを、サポートから求められたときに、自分で確認して共有できます。

## ソースコードについて

TwitchThanksLogger本体のソースコードは、現在公開していません。将来的なオープンソース化は検討していますが、現時点で予定や時期は確定していません。このリポジトリは配布物の案内用で、バージョンのタグはアプリ本体のソースを含みません。OBS Nativeプラグインについては、配布版に対応するソースおよびビルド情報を、Releaseの `TwitchThanksLogger-Native-Source-0.1.0-beta.4.zip` として提供します（[SOURCE.md](SOURCE.md)）。

## ライセンス

TwitchThanksLogger 全体に適用されるライセンスは、現時点では設定していません。このリポジトリは、プロジェクト全体がオープンソースであることを示すものではありません。

OBS Nativeプラグインには GPL-2.0-or-later の対象となるコードが含まれています。この部分に対応するソースおよびビルド情報は、該当する配布版とあわせて別途提供します。
