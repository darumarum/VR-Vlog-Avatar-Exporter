# VR Vlog lilToon VRM Exporter

[日本語](README.md) · [English](README.en.md)

[![MIT License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

lilToonのアバターを、iPhoneのVR Vlogで使う **VRM 1.0** に書き出す、MITライセンスのUnity用パッケージです。標準MToonによる互換表示と、VR Vlog向けのlilToon拡張を一つのVRMに保存します。

**[インストールページを開く](https://vrvlog.fun/exporter/)** · [使い方](#使い方) · [困ったとき](#困ったとき)

## できること

- lilToonの見た目をVR Vlogで表示できます。
- 表情・ポーズ・瞬き・顔トラッキング用の変形や、髪・衣装の揺れ物を書き出せます。
- Modular Avatarで設定した髪や衣装にも対応しています。書き出しには一時コピーを使い、元のアバターを保持します。

VRChatのギミックやすべてのシェーダー効果を再現できるわけではありません。揺れ方は近似になり、顔や体形もVRChatでの見た目と異なる場合があります。書き出したVRMをアプリで確認してください。他のVRMビューアーではMToonによる互換表示になり、見た目や動く表情が異なる場合があります。

## 必要な環境

アバターとlilToonを導入済みのUnityプロジェクトで使います。

| 項目 | 対応バージョン |
| --- | --- |
| Unity | 2022.3（VRChatプロジェクトではVCC・ALCOMが案内するバージョン） |
| lilToon | 2.0.0〜2.3.4 |
| UniVRM | 0.131.0／0.131.1／0.131.2（VCC・ALCOMでは0.131.xを自動導入） |
| VR Vlog | 0.1.1（ビルド345）以降 |

Modular Avatarを使うアバターは、Modular Avatarとその依存パッケージも事前に導入してください。

lilToon 1.x以前、2.3.4より新しい版、プレリリース版では書き出せません。対応範囲内でもシェーダーの構成が異なる場合は停止します。詳しくは[対応するlilToonの版](Compatibility/README.md#supported-liltoon-versions)を確認してください。

## インストール

1. [インストールページ](https://vrvlog.fun/exporter/)で「VCC / ALCOMに追加」を押します。
2. VCC・ALCOMで、使いたいUnityプロジェクトのパッケージ管理画面を開きます。
3. 「VR Vlog lilToon VRM Exporter」の安定版をインストールします。0.11.15は通常の一覧から選べます。

追加ボタンで開かない場合は、VCC・ALCOMのリポジトリ追加画面に次のURLを貼り付けてください。

```text
https://vrvlog.fun/exporter/index.json
```

すでに個人側・組織側のURLを登録している場合は、その登録を使い続けられます。登録し直す必要はありません。

更新前にはUnityプロジェクトをバックアップしてください。更新内容をVRMに反映するには、元のアバターから書き出し直します。[最新安定版](https://github.com/VR-Vlog/VR-Vlog-Avatar-Exporter/releases/latest)・[変更履歴](CHANGELOG.md)

<details>
<summary>ZIPで手動導入する場合</summary>

1. [インストールページ](https://vrvlog.fun/exporter/)の「ZIPで導入」から、エクスポーター・UniGLTF・VRMの3つのZIPをダウンロードします。
2. プロジェクトの `Packages` 内の別々のフォルダーへ展開し、それぞれの直下に `package.json` がある状態にします。
3. Unityで読み込みが終わるのを待ちます。同じUniVRMパッケージを重複して導入しないでください。

</details>

## 使い方

以下は安定版0.11.15の手順です。

1. Unityでアバターを開き、書き出す衣装を表示します。アバターと親オブジェクトも有効にしてください。
2. メニューの「VR Vlog → VRMを書き出す」を開きます。
3. Hierarchyのアバターの一番上のオブジェクトを「アバター」欄に指定し、「書き出しを準備」を押します。
4. 表情を使う場合は「候補ファイル」から追加します。Projectから `.anim` をドロップすることもできます。名前や「確認」を押すとプレビューできます。
5. 必要なら「標準の表情（喜怒哀楽）」を選びます。表情を追加せずに保存することもできます。
6. 任意の全身ポーズと **ライセンス設定** を確認し、**作者名** を入力して **VRMを保存** を押します。

作者名は必須です。空欄や空白だけでは保存できません。保存が完了したら「保存先を開く」でファイルを確認できます。

利用条件を設定する場合は、保存欄の **ライセンス設定** を開き、元の利用規約に合わせてプルダウンを選びます。規約URL（VN3等）、著作権表示、第三者ライセンスも入力できます。設定は出力VRMのメタデータに保存されます。設定を開かない場合は、従来の既定値（作者のみ・個人非営利・クレジット表記が必要・表現用途の各許可なし・再配布と改変なし）で書き出します。

表情・ポーズの選び方や、選択できないファイルの理由は[VRM書き出しガイド](Documentation~/ExperimentalExpressionCapture.md)にまとめています。

### iPhoneのVR Vlogで開く

1. 書き出した `.vrm` をiPhoneの「ファイル」に保存します。
2. VR Vlogの設定で「lilToon専用表示」をオンにします。
3. 「モデルを変更 → 端末のVRMを選ぶ」からファイルを選びます。表示設定を変えた場合は読み込み直してください。

QR転送を使う場合は、VRM保存後に「QRコードでスマホに送る」を押します。受信にはQR対応のiPhone TestFlight版が必要です。Android配布版では受信できません。手順や同意事項は[クラウド転送ガイド](Documentation~/CloudTransfer.md)を確認してください。

## 困ったとき

| 状況 | 確認すること |
| --- | --- |
| 動作環境の確認画面が出る | 表示された不足パッケージや未対応バージョンを確認してください。パッケージが自動で変更されることはありません。 |
| 書き出しが止まる | 「書き出しの詳細」で対象・理由・対処方法を確認してください。対策候補がある場合はコピーで試し、見た目を確認して保存できます。 |
| 瞬きが合わない | 保存欄の瞬きの「確認・調整」を開きます。自動設定できない場合は「手動」でメッシュと閉眼用の変形を選び、プレビューして適用してください。 |
| 衣装が出力されない | Unityで衣装が表示され、アバターに接続されているか確認してください。非表示の衣装は出力されません。 |
| 端末で読み込めない | モデルによっては端末のメモリ不足で読み込めない場合があります。 |

解決しない場合は、使用バージョン・再現手順・エラーを添えて[不具合報告](https://github.com/VR-Vlog/VR-Vlog-Avatar-Exporter/issues/new/choose)へお知らせください。VR Vlogアプリ内の問い合わせも利用できます。

報告には「共有用の診断」をコピーできます。「全文をコピー」「テキスト保存」の内容にはアバター名やパスが含まれるため、公開前に確認してください。脆弱性は公開Issueに書かず、[非公開の報告窓口](SECURITY.md)へ連絡してください。

## 詳しく知りたいとき

| 知りたいこと | ガイド |
| --- | --- |
| 表情・ポーズの選択と保存 | [VRM書き出しガイド](Documentation~/ExperimentalExpressionCapture.md) |
| 見た目や設定をどこまで引き継げるか | [アバターの保存](Compatibility/AvatarPreservation.md) |
| 髪・衣装の揺れ方 | [PhysBoneの変換](Compatibility/PhysBone.md) |
| 体・指のポーズとアニメーション | [ポーズ](Documentation~/HumanoidPoses.md)・[アニメーション](Documentation~/HumanoidAnimations.md) |
| 更新内容 | [変更履歴](CHANGELOG.md) |
| 開発・改善への参加 | [開発参加ガイド](CONTRIBUTING.md) |

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
