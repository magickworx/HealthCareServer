# HealthCareServer

[まいにち体調管理](https://apps.apple.com/jp/app/id1520936281?mt=8&uo=4)
アプリの JSON データを受信する API サーバのサンプル版ソースコードです。

アプリから JSON データを取得して、指定したディレクトリに保存するだけのプログラムです。基本的な機能のみの実装です。保存する部分をデータベースを使うように改良すると利便性が向上するでしょう。

``config.js`` の内容で基本的な設定を変更できます。通常はそのまま利用しても問題ないでしょう。

## 使いかた

アプリのサーバ情報画面で ``config.js`` 内の値を設定します。

- ホスト名には、サーバを起動する IP アドレスを記入します。
- ポート番号には __port__ の値を設定します。
- API のパスには __endpoint__ の値を設定します。
- 認証用トークン文字列には __accessToken__ の値を設定します。

![設定](images/screenshot001.png "サーバ情報")

## サーバの起動

`npm install` してから `npm start` で実行できます。

### JSON データの保存先

``config.js`` の __storage__ に指定したディレクトリに、アプリから受信した JSON データをそのまま保存します。

## アプリから送信

チェック画面の右上のアイコンをタップして、「全データを JSON 形式で送信」を選択します。

![送信](images/screenshot002.png "JSON データ送信")

## JSON データの構造

アプリから送信される JSON データは、以下の構造を持ちます。

```javascript
{
  "date": {
    "year": 2020,
    "month": 7,
    "day": 31
  },
  "fever_in_family": false,
  "travel_abroad": false,
  "conditions": [
    {
      "time_zones": 0,
      "body_temperature": 35.8,
      "cough": false,
      "runny_nose": false,
      "phlegm": false,
      "breathless": false,
      "sore_throat": false,
      "eye_pain": false,
      "muscle_pain": false,
      "headache": false,
      "diarrhea": false,
      "vomiting": false,
      "malaise": false,
      "smell": false,
      "taste": false,
      "antipyretic": false
    }
  ],
  "remarks": "暑いので外歩きはマスクなし"
}
```

|              変数 |  型  | 意味 | 省略 |
|------------------:|:-----|:-----|:----:|
| date              | 辞書 | 日付 | 不可 |
| fever\_in\_family | 論理 | 家族に発熱 | 不可 |
| travel\_abroad    | 論理 | 海外渡航 | 不可 |
| conditions        | 配列 | 体調データ | 不可 |
| remarks           | 文字列 | 備考 | 可 |

### date のデータ構造

| 変数  |  型  | 意味 | 省略 |
|------:|:-----|:----:|:----:|
| year  | 整数 | 年   | 不可 |
| month | 整数 | 月   | 不可 |
| day   | 整数 | 日   | 不可 |

### conditions 配列内の辞書データの構造

| 変数  |  型  | 意味 | 省略 |
|------:|:-----|:-----|:----:|
| time\_zones | 整数 | 時間帯 | 不可 |
| body\_temperature | 実数 | 体温 | 不可 |
| cough | 論理 | 咳 | 不可 |
| runny\_nose | 論理 | 鼻水 | 不可 |
| phlegm | 論理 | 痰 | 不可 |
| breathless | 論理 | 息切れ | 不可 |
| sore\_throat | 論理 | 喉の痛み | 不可 |
| eye\_pain | 論理 | 眼の痛み | 不可 |
| muscle\_pain | 論理 | 筋肉痛 | 不可 |
| headache | 論理 | 頭痛 | 不可 |
| diarrhea | 論理 | 下痢 | 不可 |
| vomiting | 論理 | 嘔吐 | 不可 |
| malaise | 論理 | 倦怠感 | 不可 |
| smell | 論理 | におい | 不可 |
| taste | 論理 | 味 | 不可 |
| antipyretic | 論理 | 解熱剤の服用 | 不可 |

#### time\_zones の値と意味

| 値  | 意味 |
|:---:|:-----|
|  0  | 朝   |
|  1  | 昼   |
|  2  | 夕   |
|  3  | 就寝前 |


## ライセンス

Copyright (c) 2020, Kouichi ABE (WALL) All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

 1. Redistributions of source code must retain the above copyright notice,
    this list of conditions and the following disclaimer.

 2. Redistributions in binary form must reproduce the above copyright notice,
    this list of conditions and the following disclaimer in the documentation
    and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
