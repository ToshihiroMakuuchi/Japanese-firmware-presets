# Betaflight 日本語プリセット (まっくさんプリセット)

2022/03/30 更新:  
今回、Betaflight公式となるlimonspb氏のリポジトリをフォークし、日本語化したプリセットを独断と偏見？で勝手に提供を開始しますｗ
基本的には公式プリセットは定期的にマージしていく予定ですが、日本ユーザ向けに独自のプリセットを積極的に公開してまいります。
まずはBetaflight Configurator 10.8.0(-RC3)をインストールし、下記手順で設定いただければ幸いです。

## [【まっくさんプリセット】の設定方法](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/wiki/%E3%80%90%E3%81%BE%E3%81%A3%E3%81%8F%E3%81%95%E3%82%93%E3%83%97%E3%83%AA%E3%82%BB%E3%83%83%E3%83%88%E3%80%91%E3%81%AE%E8%A8%AD%E5%AE%9A%E6%96%B9%E6%B3%95)


# ファームウェアプリセット

プリセットは、Betaflightフライトコントローラにおけるファームウェア設定をより簡単に行う方法です。

- [イントロダクション](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/blob/ToshihiroMakuuchi/Japanese-presets/README_JP.md#イントロダクション)
- [プリセットの適用と利用方法](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/blob/ToshihiroMakuuchi/Japanese-presets/README_JP.md#プリセットの適用と利用方法)
- [プリセット開発者へのフィードバック](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/blob/ToshihiroMakuuchi/Japanese-presets/README_JP.md#プリセット開発者へのフィードバック)
- [カスタム・プリセットソース](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/blob/ToshihiroMakuuchi/Japanese-presets/README_JP.md#カスタムプリセットソース)
- [新規プリセットの作成](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/blob/ToshihiroMakuuchi/Japanese-presets/README_JP.md#新規プリセットの作成)
- [既存プリセットの修正](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/blob/ToshihiroMakuuchi/Japanese-presets/README_JP.md#既存プリセットの修正)
- [プリセット仕様](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/blob/ToshihiroMakuuchi/Japanese-presets/README_JP.md#プリセット仕様)
- [クレジット](https://github.com/ToshihiroMakuuchi/Japanese-firmware-presets/blob/ToshihiroMakuuchi/Japanese-presets/README_JP.md#クレジット)


## イントロダクション

Betaflightプリセットシステムは、ユーザがファームウェア設定を構成・変更するための『スニペットな(ちょっとした)』CLIを簡単に見つけて適用できるようにします。

またすべてのプリセットは、一般公開される前に、チェックと承認プロセスを経て公開されています。

>警告：プリセットを保存すると、コンフィグ設定が書き換えられてしまいます！ユーザは以前の設定のバックアップを作成し、バックアップから設定を復元する方法を把握しておく必要があります。


## プリセットの適用と利用方法

- 現在の設定のバックアップを取得する (【CLI】タブへ移動し`dump all`と入力し、その表示されたデータを安全な場所に保存)
- 【プリセット】タブに移動する
- 適用したいプリセットを検索しクリックする
- 説明を読み、オプションで`オンラインで表示`をクリックして変更点を確認する
- 利用可能な`オプション`の中からチェックボックスを選択する
- `選択`をクリックする - CLIに設定が書き込まれる
- `保存と再起動`をクリックすると変更内容が恒久的にファームウェアに書き込まれる (元に戻す機能はありません)

プリセットによって変更したくない定義が変更された場合【プリセットを適用する前に】それらの変更点をメモしておき、後でCLIで手動で変更し直してください。例えば、複雑なプリセットに不要なレートの変更が含まれているような場合、既存のレートを事前にメモしておき、プリセットを適用・保存し、新たなレートで試してみてください。新たなレートが気に入らない場合は手動で元の設定に戻します。

保存する前に複数のプリセットを順次適用することができます。 同じ項目に対して複数のプリセットを適用した場合は、最後に適用したプリセットが優先されます。

【プリセット】タブから抜けた後は、通常FCに再接続する必要があります。これはプリセットシステムがCLIと相互関係にあるため、CLIから一旦外れた場合はFCへ再接続する必要があります。


## プリセット開発者へのフィードバック

現在、フィードバックを提供する最良の方法は、プリセット作成したプルリクエストにコメントを追加することです。プリセット適用ウィンドウの `ディスカッション` ボタンを押してGitHubの対象のプルリクエストに移動してください。

または [Firmware Presets Pull Request page](https://github.com/betaflight/firmware-presets/pulls) を検索してください。


## カスタム・プリセットソース

開発者やチューナーは、Betaflight Configurator にプリセットリンクを自分の GitHub リポジトリへ追加することができます。これにより、開発者はプルリクエストを提出する前にローカル環境でプリセットをテストでき、チューナーやFCボード開発元はカスタムプリセットを開発・共有することができ、個人では自分自身の個別プリセットのオンラインバックアップを保持することが可能となります。

手順は以下の通りです:
- betaflight/firmware-presets リポジトリを GitHub アカウントにクローンする
- Masterとは別のブランチを作成し、そこに自分用のプリセットを作成する
- `node indexer/indexer.js` `node indexer/check.js` を実行する
- 作成したブランチを GitHub にプッシュする

カスタム・プリセットソースを使用する場合:
- Betaflight Configuratorにて、【プリセット】タブ ⇒ プリセットソースをクリックする
- URL項目にて `https://github.com/sourceGithubAccountName/firmware-presets/`` に設定する
- GitHubブランチ項目に、プッシュしたブランチ名を設定する

エンドユーザは誰でも貴方が提供するカスタムプリセットを適用できます。

独自に作成したブランチが Betaflight に対応するように master にRebaseしない限り、既存プリセットは古くなってしまう場合がありますのでご注意ください。

他のプリセットをすべて削除して、自分自身が作成したプリセットだけを残すようにすることもできますし、ディレクトリ構造を置き換えたり、削除したりすることもできます。ファイルやディレクトリを変更した場合は、インデックスファイルを再ビルドして Github にプッシュする必要があります。


## 新規プリセットの作成

**新規プリセットの投稿** はGitHubの [Firmware Preset Pull Request](https://github.com/betaflight/firmware-presets/pulls) でプルリクエストを行う必要があります:
- プリセット毎にプルリクエストが必要です。
- すべてのプリリクエストは Betaflight の開発者によって慎重に評価されます。
- 承認は自動的ではなく、お時間を要す場合があります。
- CLI名とプリセット値はバージョンごとに変わるので、通常4.2または4.3用に別々のプリセットを作成するのが最良です。
- プリセットは [specifications](https://github.com/betaflight/firmware-presets#preset-specifications) に準拠し、何が変更されるかを簡潔に記述しなければなりません。

プリセットを作成する際、既存の設定に追加するような変更方法は、基本的に4つの手法で適用します:
- **1つまたは複数の値において** PID値やパラメータ値をデフォルト値より高い値に設定する等、積極的に目標達成するための新しい値に置き換えたり、強制的に上書きを実施します。
- **いくつかの値を強制的にオフまたはデフォルト値に戻す** ことで、ユーザの以前の設定に関係なく、これらの設定を無効化ないしデフォルト値となるように変更します。このためには、プリセット内でパラメータをオフまたはデフォルト値に設定する行が必要、または有効化となる変更を適用する前にデフォルトファイルを `including` する(読み込む)必要があります。変更前にデフォルトファイルを読み込ませることで、有効となる変更を書き込む前の『白紙の状態』を提供します。しかしながら、必要以上の変更を加えてしまう可能性もあります。読み込まれたデフォルトファイルが本当に必要となる変更だけを行い、ユーザが保持したいと思う設定や、プリセットに無関係な設定と干渉しないことを常に確認してください。
- **いくつかの値を無視する** またはプリセットでそれらのパラメータ値に言及しないようにすることで、ユーザ設定に含まれるどんな値でも、プリセットに必要としない値を変更しないようにします。
- **チェックボックスを提供する** ことで、例えばノイズの多い設定やクリーンな初期設定に適した代替フィルター設定を選択したり、機体にスラストリニア有効化を選択できるようにしたりします。これは `オプション` 命令で実施・有効とすることができます。

プリセットは、特定の値に設定必要とする値を上書きしたり、オフにする必要があるパラメータ値に対して設定無効化またはオフにしたり、必要に応じて(現状設定とは異なる)代替設定を選択できるようチェックボックスを提供する機能があります。

**プルリクエストの最終提出の前に**、以下の方法でプリセットを確認します:
- 使用しているPCに `node.js` をインストールする
- ドラフトの作業ディレクトリからターミナルウィンドウにて `node indexer/check.js` を実行します。チェッカーは `OK` を返します。そうでない場合はエラーを修正してからもう一度お試しください。

また `ディスカッション` 項目にプルリクエストのURLを含めることを忘れずに実施ください。

**承認された後**と作成者について:
- プルリクエストへのコメントを通じ、ユーザからのフィードバックに必ず対応してください。
- 採用された場合、貴方は将来のBetaflightファームウェアのリリースとの互換性を維持する責任があります。


## 既存プリセットの修正

プリセットは作成者の許可の有無に関わらず、その後のプルリクエストによって変更することができます。

既存プリセットを修正するプルリクエストは、元のプルリクエストにリンクされていなければなりません。そうすることで作成者は提案された変更通知を受け取ることができます。


## プリセット仕様

プリセットは、以下の仕様に準拠した項目と、データ本体として1つ以上の『スニペットな(ちょっとした)』CLI値が含まれる必要があります。


### 項目について

**必須項目**
```
 TITLE, FIRMWARE_VERSION, CATEGORY, STATUS
```

**オプション項目**
```
    KEYWORDS, AUTHOR, DESCRIPTION, INCLUDE, OPTION, FORCE_OPTIONS_REVIEW, OPTION_GROUP BEGIN, DISCUSSION, DISCLAIMER, INCLUDE_DISCLAIMER, WARNING, INCLUDE_WARNING, HIDDEN
```
すべての項目タグは必ず…:
- 先頭に `#$ ` が付き、
- `大文字であること`、そして
- コロン `:` で終わること。(但し `OPTION END` タグはコロンなし)
- 例 `#$ KEYWORDS:`

| 項目 | 内容 |
| ----------- | ----------- |
| File name | ユニーク、簡潔な説明、作成者を含むよう、またスペースは使わずアンダーバーとしてください。 例：rece_4in_ctzsnooze |
| TITLE | 明確で完結な説明、プリセットの主な特徴を含むようにしてください。 |
| FIRMWARE_VERSION | 対応バージョン毎に1行、必要な行数だけ記載してください。すべてのCLIコマンドは、記載されているファームバージョンで読み取り可能であることを確認してください。一致しないCLIコマンドはエラーを返します。もしプリセット内で2種のBFバージョンで同じコマンドを稼働させるよう内包し、2種をサポートしようとする場合は、一般的にエラーが発生することをユーザに説明してください。 |
| CATEGORY | 下記のカテゴリ一覧をご覧ください。承認されたカテゴリ名のみ受け付けます。 |
| STATUS | Betaflightチームが開発したプリセットは `OFFICIAL` 、ユーザから提供されたプリセットは `COMMUNITY` 、開発中のプリセットは `EXPERIMENTAL` としてください。 |
| KEYWORDS | 慎重に定義してください。プリセットを使用するユーザを想定し、そのユーザが使用しそうなキーワードを付け検索し易いようにします。各項目はコンマ区切りとしてください。 |
| AUTHOR | 作成者のGitHub名、またはニックネームを指定します。 |
| DESCRIPTION| 何が変更されるのか、また関連する場合は何が変更されないのかを明確に説明します。例えば、フィルターの設定にRPMフィルターが必要な場合は、必ずその旨を明記してください。`#$ DESCRIPTION:` 行を各々記載した場合は、それぞれ別段落となります。`(空白)#$ DESCRIPTION:` の行は段落の間に空白行が入ります。すべてのDESCRIPTION行は、INCLUDE行SやOPTION行の上に配置しなければなりません。 |
| FORCE_OPTIONS_REVIEW | プリセットを適用する前にオプションを確認していない場合は、オプションを確認するダイアログが表示されます。 |
| INCLUDE | このプリセットのCLIコマンドの前に、1つまたは複数の別のプリセットからのデータを挿入します。コマンドの前にデフォルト値を強制入力するのに便利です。詳細は以下を参照してください。 |
| OPTION | `OPTION` タグの中にあるコマンドは、そのコマンドを適用するかしないかのチェックボックスをユーザに表示します。チェックボックスのデフォルトの動作を指定することができます。各 `OPTION` には一意な名前を付けなければなりません。詳しくは [こちら](https://github.com/betaflight/firmware-presets#OPTION) をクリックしてください。 |
| OPTION_GROUP | オプショングループの前に表示するテキストです。 |
| DISCLAIMER | 免責事項のテキストを含む項目です。 |
| INCLUDE_DISCLAIMER | `presets/` から始まる免責事項のテキストを含むファイルへのパスを記載します。 |
| WARNING | 警告のためのテキスト項目です。プリセットを承認する前の最終ダイアログを意図しています。 |
| INCLUDE_WARNING | `presets/` から始まる警告のテキストを含むファイルへのパスを記載します。機能的には警告と同じです。 |
| DISCUSSION | プリセットのフィードバックとディスカッションのページにリンクするURL項目です。現在プリセットを生成したプルリクエストの URL に設定する必要があります。 |
| HIDDEN | `#$ HIDDEN: true` は、プリセットがインデックスに登録されるのを防ぎ、プリセットのユーザ検索を防ぎます。他のプリセットにのみINCLUDEされる『見えない』プリセットとして存在させます。 |

### プリセットの構成例:

```
#$ TITLE: 7in long range cinematic by userx
#$ FIRMWARE_VERSION: 4.2
#$ FIRMWARE_VERSION: 4.3
#$ CATEGORY: TUNE
#$ STATUS: EXPERIMENTAL
#$ KEYWORDS: word1, word2, word3
#$ AUTHOR: Name Lastname / Pilotname
#$ DESCRIPTION: Description paragraph1
#$ DESCRIPTION: Description pagagraph2  (as many description paragraphs as needed)
#$ DISCLAIMER: Text of disclaimer (mandatory for VTx Presets)
#$ WARNING: Text of warning
#$ DISCUSSION: https://github.com/betaflight/firmware-presets/pull/nn
#$ FORCE_OPTIONS_REVIEW

#$ INCLUDE: presets/4.3/rates/defaults.txt

<cli command 1>
<cli command 2>
....
<cli command n>

#$ OPTION BEGIN (CHECKED): Region 1 name
<cli command n + 1>
<cli command n + 2>
...
<cli command m>
#$ OPTION END

#$ OPTION_GROUP BEGIN: This group name
#$ OPTION BEGIN (UNCHECKED): Region 2 name
<cli command m + 1>
<cli command m + 2>
#$ OPTION END
#$ OPTION BEGIN (UNCHECKED): Region 3 name
<cli command j + 1>
<cli command j + 2>
<cli command j + 3>
#$ OPTION END
#$ OPTION_GROUP END
```

### カテゴリ

すべてのプリセットには、次のいずれかのカテゴリを割り当てる必要があります:
```
    TUNE, RATES, FILTERS, RC_LINK, RC_SMOOTHING, OSD, VTX, LEDS, MODES, OTHER, BNF
```

| カテゴリ | 内容 |
| ----------- | ----------- |
| TUNE | PIDパラメータとTPA、アンチグラビティ、スラストリニアなどのサブパラメータ、RPMフィルタリングを含むフィルターパラメータを定義します。モーター出力リミット、スロットルカーブ/スケール、フィードフォワードブースト、フィードフォワード遷移またはリミット、Vbat サグ値補正、スロットルブースト等のパラメータがあります。 `RCリンク` や `RCスムージング` 設定は、リージョンで提供されない限りデフォルトでチェックされないため、値として設定すべきではありません。 |
| RATES | レートタイプと、レートに影響する値です。(rc_rate、expo、s_rate) スロットルカーブ設定、レートリミット、レベルエクスポ設定を変更する場合は、別のプリセットで提供する必要があります。レート名は、オプションのdefault-off Regionにて指定することができます。TPAはレートプリセットに含まれず `TUNE` パラメータに含まれます。 |
| FILTERS | 特定のタイプの機体に合うように最適化されたフィルター設定です。フィルターの最適化は、RPMフィルタリングが有効か否かに大きく依存するため、名称と説明にRPMフィルタリングが有効であることを明記する必要があります。RPMフィルタリングが利用できない場合のために、リージョンでは代替設定を提供することができます。 |
| RC_LINK | リンクの種類(シリアル、PPM)、使用プロトコル(SBUS、CRSF、Spektrum等)、テレメトリー設定、単位、精度設定等、リンク速度に合わせて設定する必要があるフィードフォワード平均化とフィードフォワードスムージング、フィードフォワードジッター設定等が指定できます。異なる速度に設定可能なRCリンクには、別のプリセットまたはリージョンを使用することができます。 |
| RC_SMOOTHING | RCスムージング設定は、スティックの急激な変化に対する即応性を変化させます。オート設定では、レース用からシネマティック撮影用までのあらゆるレベルのスムージング設定が可能ですが、オート設定の最終的なスムージング量はRCリンク速度に依存します。手動設定は、より広い範囲のRCリンク速度で、より一貫した滑らかさを提供します。 |
| OSD | OSDに関連するパラメータコレクションです。セル電圧表示、デバッグモードなど、OSDに表示されるものに影響を与える設定を含みます。 |
| VTX | VTXtableまたは関連する設定です。注:1の下記免責事項が含まれていなければなりません。 |
| LEDS | LED設定の項目です。 |
| MODES | モードスイッチと詳細設定の項目です。 |
| OTHER | 複数のカテゴリ設定を含むプリセット、または他カテゴリに容易に分類できない設定のためのプリセットです。例：RATE、TUNE、RC_LINK、LEDS設定を複合的に含む全体設定、またはGPS、ローンチコントロール、カメラ制御、または同様の値等。 |
| BNF | (機体)完成品の出荷設定等です。RCリンク、RCスムージング、その他の設定の代替オプションを提供するためにリージョンを使用することができます。 |

注1：VTXプリセットでは、以下の免責事項が必須となります:
> このプリセットで提供される情報は、金銭上の利益なく、専ら個人的な興味により行う自己訓練、通信および技術研究のための目的のみとなります。Betaflightは、ここで提供されるいかなる情報の使用の安全性または合法性に関して示すものではありません。エンドユーザは、関連するすべての法令および規制に準拠、該当していることを確認するすべての責任および義務を負うものと致します。
>
> このVTX設定およびVTXtable設定は、日本のバンドプランに沿った利用が必須となり、示された周波数以外は法令違反となりますのでご注意ください。日本国内での5.8GHz帯利用は5,690～5,725MHz、5,730～5,755MHｚ、5,757～5,760MHz、5,762～5,765MHz、5,770～5,810MHzが使用可能です。この周波数帯を利用する場合はアマチュア無線の資格を有し国内の技術基準に合致した無線設備を利用、原則、総務大臣の免許を受け無線局を開設することが必要となります。


### モータープロトコルの設定
プリセット作成者は、TUNE、FILTERS、OTHER、BNFのプリセットカテゴリの中で `#$ OPTIONS` 以外でもモータープロトコルを指定することが可能です。

`set motor_pwm_protocol = .....`

**但し、この場合は安全のために適切な `#$ WARNING:` または `#$ INCLUDE_WARNING:` を設定しなければなりません** DSHOTをサポートしていないESCでDSHOT等を設定すると、アーミングせずにすぐにモーターを回転させてしまい、非常に危険であることをユーザやプリセット作成者は認識する必要がありますのでご注意ください。

注：default.txtは、いずれもモータープロトコルをリセットするものではありません。


### INCLUDE(インクルード)
現在のプリセットに含まれる他のプリセットへのオプションパスを指定します。

パスはプリセットディレクトリのルートからのフルパスである必要があります。

- C/C++の `#include` 関数のように動作します。
- 連続した `INCLUDE` ステートメントにより複数のプリセットを適用することができます。
- `INCLUDE` の再帰性がサポートされます。
- `INCLUDE` プリセットのメタプロパティは無視されます。

Example:  `#$ INCLUDE: presets/4.3/category/preset_x.txt`


### OPTION(オプション)
`OPTION` タグは、ユーザが適用ダイアログのドロップダウンリストから簡易なチェックボックスで設定グループを適用できるようにします。各 `OPTION` はドロップダウンリストの1行目を挿入します。`OPTION` リストではテキストや空白行を使用することはできません。

プリセット作成者は、チェックボックスの初期のチェック有無を設定し、チェックボックスの横にあるラベルを指定します。

もし作成者がユーザにオプションを見直すように警告したいようであれば、ヘッダにこの行を挿入することにより『このプリセットを選択する前に、オプションリストを確認してください。』というダイアログを表示させることができます:
```
#$ FORCE_OPTIONS_REVIEW: TRUE
````

オプションは、C#のプリプロセッサ命令文 `#region` に似た動作となります。

`OPTION` が有用な例としては `BNF` や `TUNE` のプリセットがあります。プリセットはSBUS、Crossfire、Ghostなどの異なる送信プロトコルのための異なるオプションを提供することが可能です。ユーザはプリセットが適用されたときに使用する送信プロトコルを選択できます。

例えばレース用、HDフリースタイル用、シネマティック用など、異なるRCスムージングの設定を、同一の全体チューニングの中で一元的に提供することができます。

また個別の設定、例えばモーター出力の制限を保持したい場合はTUNEを適用する際に、その値を特定の値として設定することもできます。その場合、チューナーはその値を適用するオプションを付加することができますが、ユーザはその提案を受け入れることはできません。

`OPTION` 領域は `#$ OPTION BEGIN: <option name>` タグで始まり `#$ OPTION END` タグで終わらなければなりません。対象となるCLI行のデータ本体はこれらのタグの間に配置します。`option name` は左側にチェックボックスとともに表示され、選択するとCLI行がロードされます。

チェックボックスのデフォルト状態は `(CHECKED)` または `(UNCHECKED)` のいずれかを設定します。プリセットで先にデフォルト値にリセットされていないCLIの値は `UNCHCHKED` でなければなりません。

オプションは、この構文を使って『title』または『group name』の下に『grouped(グループ化)』することができます。

```
#$ OPTION_GROUP BEGIN: your group name
<options>
#$ OPTION_GROUP END
````

完全な `OPTION` の構文例は以下のようになります:
```
#$ OPTION_GROUP BEGIN: this group name
#$ OPTION BEGIN (UNCHECKED): <Option1 name>
CLI payload strings
#$ OPTION END
#$ OPTION BEGIN (UNCHECKED): <Option2 name>
CLI payload strings
#$ OPTION END
#$ OPTION_GROUP END
```

注1: `OPTION` タグのネスト(入れ子)はサポートされていません。

注2：プリセットにオプションがある場合、プリセットの各リージョンに『dummy』オプションタグがあらかじめ定義されていなければ、これらのオプションはユーザには表示されません:

```
#$ OPTION BEGIN: <first_option_name_from_preset_x>
#$ OPTION END
#$ OPTION BEGIN: <second_region_name_from_preset_x>
#$ OPTION END
(for however many options exist in preset_x that you want to provide)
#$ INCLUDE: presets/4.3/category/preset_x.txt
```

## クレジット

このプリセットシステムは  @limonspb 氏がBetaflight 4.3用に開発されたものです。

