# VR Vlog lilToon VRM Exporter

[日本語](README.md) · [English](README.en.md)

## インストール

**[インストールページを開く](https://vrvlog.fun/exporter/)**

1. 「VCC / ALCOMに追加」を押す。
2. VCC・ALCOMで、使いたいプロジェクトのパッケージ管理画面を開く。
3. 「VR Vlog lilToon VRM Exporter」の安定版をインストールする。

[使い方](#使い方) · [iPhoneで開く](#iphoneで開く) · [困ったとき](#困ったとき)

### 対応環境

| 必要なもの | バージョン |
| --- | --- |
| Unity | 2022.3 |
| lilToon | 2.0.0〜2.3.4 |
| UniVRM | 0.131.0／0.131.1／0.131.2 |
| VR Vlog | 0.1.1（ビルド345）以降 |

- **事前に用意：** アバターとlilToon。
- **自動導入：** VCC・ALCOMではUniVRM 0.131.xを導入します。
- **Modular Avatarを使う場合：** 本体と依存パッケージも必要です。
- **VRChatプロジェクト：** UnityはVCC・ALCOMが案内する版を使ってください。

---

**注意：更新する場合**

先にUnityプロジェクトをバックアップしてください。
更新後は、元のアバターからVRMを書き出し直します。

**注意：対応外のlilToon**

1.x以前・2.3.4より新しい版・プレリリース版は対象外です。
対応版でも、シェーダーの構成によっては停止します。
[互換性の詳細](Compatibility/README.md#supported-liltoon-versions)

---

<details>
<summary>追加ボタンで開かない場合</summary>

VCC・ALCOMのリポジトリ追加画面に、次のURLを貼り付けてください。

```text
https://vrvlog.fun/exporter/index.json
```

以前の個人側・組織側のURLを登録済みなら、そのまま使えます。

</details>

<details>
<summary>ZIPで手動導入する場合</summary>

1. [インストールページ](https://vrvlog.fun/exporter/)の「ZIPで導入」を開く。
2. エクスポーター・UniGLTF・VRMの3つのZIPをダウンロードする。
3. `Packages` 内の別々のフォルダーへ展開する。
4. 各フォルダーの直下に `package.json` があることを確認する。
5. Unityの読み込みが終わるのを待つ。

**注意：** 同じUniVRMパッケージを重複して導入しないでください。

</details>

## 使い方

安定版0.11.15の手順です。

### 1. アバターを準備

Unityで、書き出すアバターと衣装を表示します。
親オブジェクトも有効にしてください。

### 2. 書き出し画面を開く

メニューの「VR Vlog → VRMを書き出す」を選びます。

### 3. アバターを指定

Hierarchyのアバター最上位を「アバター」欄に指定します。
「書き出しを準備」を押します。

### 4. 表情を追加（任意）

- **追加：** 「候補ファイル」から選択。`.anim` のドロップでも追加できます。
- **確認：** 表情名か「確認」を押すとプレビューできます。
- **喜怒哀楽：** 「標準の表情（喜怒哀楽）」で選択します。

表情を追加せずに保存することもできます。

### 5. 保存

任意の全身ポーズと **ライセンス設定** を確認し、**作者名** を入力して **VRMを保存** を押します。

保存後は「保存先を開く」でファイルを確認できます。

---

**注意：作者名は必須**

空欄や空白だけでは保存できません。

**ライセンス設定**

利用条件を設定する場合は、保存欄の **ライセンス設定** を開き、元の利用規約に合わせてプルダウンを選びます。規約URL（VN3等）、著作権表示、第三者ライセンスも入力できます。設定は出力VRMのメタデータに保存されます。設定を開かない場合は、従来の既定値（作者のみ・個人非営利・クレジット表記が必要・表現用途の各許可なし・再配布と改変なし）で書き出します。

---

## iPhoneで開く

1. `.vrm` をiPhoneの「ファイル」に保存する。
2. VR Vlogの設定で「lilToon専用表示」をオンにする。
3. 「モデルを変更 → 端末のVRMを選ぶ」でファイルを選ぶ。

**注意：** 表示設定を変えた場合は、VRMを読み込み直してください。

<details>
<summary>QRコードで転送する場合</summary>

VRM保存後に「QRコードでスマホに送る」を押します。

**注意：受信できるアプリ**

- iPhone：QR対応のTestFlight版が必要です。
- Android：配布版では受信できません。

[転送手順・同意事項](Documentation~/CloudTransfer.md)

</details>

## 困ったとき

### 書き出せない

「書き出しの詳細」で、対象・理由・対処方法を確認してください。
対策候補があればコピーで試せます。見た目を確認して保存してください。

### 動作環境の確認画面が出る

不足パッケージや未対応バージョンを確認してください。
パッケージが自動で変更されることはありません。

### 衣装が出ない

衣装の表示と、アバターへの接続を確認してください。
非表示の衣装は出力されません。

### 瞬きが合わない

保存欄の「確認・調整」を開きます。
自動設定できない場合は「手動」で閉眼用の変形を選んでください。
プレビューで確認してから適用します。

### 解決しない

[不具合報告](https://github.com/VR-Vlog/VR-Vlog-Avatar-Exporter/issues/new/choose)に、次の内容を添えてください。

- 使用バージョン
- 問題が起きるまでの操作
- 「共有用の診断」

VR Vlogアプリ内からも問い合わせできます。

---

**注意：ログを公開する前に**

「全文をコピー」「テキスト保存」には、アバター名やパスが含まれます。
公開前に内容を確認してください。

脆弱性の報告は[非公開の窓口](SECURITY.md)へお願いします。

---

## 書き出せるもの・制限

**対応：** lilToonの見た目、表情、ポーズ、瞬き、顔トラッキング用の変形、髪・衣装の揺れ物。

Modular Avatarの髪・衣装にも対応しています。
書き出しには一時コピーを使い、元のアバターを保持します。

**注意：完全には再現できないもの**

- VRChatのギミックや、一部のシェーダー効果。
- 揺れ方。近似になるため、元の動きと異なります。
- 顔や体形。VRChatでの見た目と異なる場合があります。
- 他のビューアーでの表示。MToon表示になり、見た目や表情が変わる場合があります。

書き出したVRMは、使うアプリで確認してください。
モデルによっては、端末のメモリ不足で読み込めない場合もあります。

## 詳細ガイド

| 調べたいこと | 文書 |
| --- | --- |
| 表情・ポーズの保存 | [書き出しガイド](Documentation~/ExperimentalExpressionCapture.md) |
| 見た目の引き継ぎ | [アバターの保存](Compatibility/AvatarPreservation.md) |
| 揺れ物 | [PhysBone](Compatibility/PhysBone.md) |
| ポーズ・アニメーション | [ポーズ](Documentation~/HumanoidPoses.md)・[アニメーション](Documentation~/HumanoidAnimations.md) |
| 更新内容 | [最新安定版](https://github.com/VR-Vlog/VR-Vlog-Avatar-Exporter/releases/latest)・[変更履歴](CHANGELOG.md) |
| 開発への参加 | [開発参加ガイド](CONTRIBUTING.md) |

## このパッケージについて

lilToonのアバターを、iPhoneのVR Vlogで使う **VRM 1.0** に書き出す、MITライセンスのUnity用パッケージです。標準MToonによる互換表示と、VR Vlog向けのlilToon拡張を一つのVRMに保存します。

[![MIT License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

| ディレクトリ | 内容 |
| --- | --- |
| `ThirdPartyNotices/` | 第三者コード・ライブラリの出典とライセンス |

## ライセンス

エクスポーターのコードは[MIT License](LICENSE)で公開しています。第三者コード・依存パッケージの出典とライセンスは、それぞれの文書を参照してください。

- [lilToon由来のシェーダー処理](ThirdPartyNotices/lilToon.md)
- [UniVRM／UniGLTF](ThirdPartyNotices/UniVRM.md)
- [転送用のBouncy Castle・ZXing.Net](ThirdPartyNotices/LanTransfer.md)（0.11.15の安定版にも同梱）
- [Avatar Optimizerの明示的な修正パッチ](Documentation~/DependencyPatches/README.md)・[同梱ライセンス](Documentation~/DependencyPatches/AAO-LICENSE.txt)

アバターなどの素材・掲載画像には各権利者の利用条件が適用されます。[画像の出典・クレジット](Website/assets/README.md)
