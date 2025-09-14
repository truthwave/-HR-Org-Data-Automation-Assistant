<p align="center">
<img width="1536" height="1024" alt="人事データの整備、GPTでここまでできる。" src="https://github.com/user-attachments/assets/0073ae8f-9dbb-4eb5-9b18-9c1e9b17cda2" />

</p>

---

# 人事・部署・役職データ処理アシスタント

> **「面倒な人事データ管理も、GPTでサクッと補助！」**

---

## 🚀 使用方法 / How to Use

1. ChatGPTにアクセスし、以下のリンクを開きます  
   👉 [HR & Org Data Automation Assistant](https://chatgpt.com/g/g-686cbd4b28c881918e461fb62a7e3c32-ren-shi-bu-shu-yi-zhi-tetachu-li-asisutanto)

2. 以下のような内容を入力します：

   ```
   部長は部署ごとに1名、副部長も1名まで。
   課長・課長代理は課ごとに1名ずつに制限したい。
   このルールをMUMPSでチェックする関数を作りたい。
   ```

3. 出力されたコードやレイアウト提案を参考に、業務に活用してください。

※このリポジトリはコード実行を前提としていません。ChatGPT上で動作するツールの説明用です。

---

## 📌 概要 / Overview

**人事・部署・役職データ処理アシスタント** は、人事・総務部門や情シス部門の社員データ管理や役職構造の整備など、現場でよく発生する課題をサポートするGPTベースの業務支援ツールです。

---

## 主な機能 / Features

### ✅ 人事データの整形・フォーマット作成
- CSV項目構成やテンプレート提案
- 社員番号、氏名、部署コード、役職名などのレイアウト設計

### ✅ 役職制限ロジック生成
- 部署・課単位での役職上限設定
- MUMPS・SQL・擬似コード出力

### ✅ 人事業務フローの設計支援
- 異動、昇格、退職時の処理手順提案

### ✅ コードサンプル生成
- MUMPS / SQL / Python による実用コード出力

### ✅ データ統合・重複検出支援
- 統合ロジック・集計・重複検出の支援

---

## 📸 **体験イメージ**
![デモ動画](https://github.com/TomoProgrammingDayori/-HR-Org-Data-Automation-Assistant/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88/%E3%83%87%E3%83%A2%E5%8B%95%E7%94%BB.gif)

![在籍・退職などのステータスでフィルタ＆色分けする方法](https://github.com/TomoProgrammingDayori/-HR-Org-Data-Automation-Assistant/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88/%E5%9C%A8%E7%B1%8D%E3%83%BB%E9%80%80%E8%81%B7%E3%81%AA%E3%81%A9%E3%81%AE%E3%82%B9%E3%83%86%E3%83%BC%E3%82%BF%E3%82%B9%E3%81%A7%E3%83%95%E3%82%A3%E3%83%AB%E3%82%BF%EF%BC%86%E8%89%B2%E5%88%86%E3%81%91%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95.jpeg)

![部署ごとに並べ替えの整理手順](https://github.com/TomoProgrammingDayori/-HR-Org-Data-Automation-Assistant/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88/%E9%83%A8%E7%BD%B2%E3%81%94%E3%81%A8%E3%81%AB%E4%B8%A6%E3%81%B9%E6%9B%BF%E3%81%88%E3%81%AE%E6%95%B4%E7%90%86%E6%89%8B%E9%A0%86.jpeg)

![部署ごとの人数をピボットテーブルで集計](https://github.com/TomoProgrammingDayori/-HR-Org-Data-Automation-Assistant/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88/%E9%83%A8%E7%BD%B2%E3%81%94%E3%81%A8%E3%81%AE%E4%BA%BA%E6%95%B0%E3%82%92%E3%83%94%E3%83%9C%E3%83%83%E3%83%88%E3%83%86%E3%83%BC%E3%83%96%E3%83%AB%E3%81%A7%E9%9B%86%E8%A8%88.jpeg)

---

## 想定ユーザー / Target Users

- 人事・総務担当者
- 情報システム部門の担当者
- MUMPSを扱う医療・金融系エンジニア
- 中小企業のIT管理者

---

## 使用例 / Usage Examples

### ✅ 入力例（役職制限ロジック生成）
```
部長は部署ごとに1名、副部長も1名まで。
課長・課長代理は課ごとに1名ずつに制限したい。
このルールをMUMPSでチェックする関数を作りたい。
```

### 🔧 GPT の出力例（MUMPS）
```mumps
CHKROLE(DEPT,KAKU,YAKU) ; 役職制限チェック関数
   NEW CNT,MAX
   SET MAX("部長")=1, MAX("副部長")=1
   SET MAX("課長")=1, MAX("課長代理")=1
   SET CNT=$O(^SYST_社員番号(DEPT,KAKU,YAKU,""),-1)
   IF CNT'<MAX(YAKU) QUIT 0
   QUIT 1
```

### ✅ 入力例（CSVレイアウト生成）
```
社員台帳のCSVレイアウトを作りたい。
社員番号、氏名、所属部署、役職を含めたい。
```

### 📄 GPT の出力例（CSVレイアウト）
| 項目名  | データ型 | 必須  |
| ---- | ---- | --- |
| 社員番号 | 数値   | Yes |
| 氏名   | 文字列  | Yes |
| 所属部署 | 文字列  | Yes |
| 役職   | 文字列  | Yes |

---

## 技術的ポイント / Technical Highlights

- **カスタムプロンプト設計**：人事ルールや構造を反映した出力設計
- **MUMPS対応**：医療・金融系のレガシー言語にも対応
- **セキュリティ配慮**：実データ非入力を想定したUI設計
- **ノーコード〜開発者層対応**：リスト/表/コード形式など多様な出力形式

---

## 注意事項 / Disclaimer

- 実在する個人情報は絶対に入力しないでください。
- 本ツールは参考情報の提供を目的としており、業務適用時は専門家の判断を優先してください。

---

## 今後の展望 / Future Plans

- Excel VBA対応の強化
- 英語版対応（国際企業向け）
- テンプレートの種類追加
- 法改正情報の自動反映対応

---

## 👨‍💻 開発者 / My Role

- 人事領域に特化したプロンプト設計
- UXを意識した出力構造・表現
- MUMPS等ニッチ技術にも対応

---

## 🧑‍💻 作者

**[Truth Wave ― 真理の波](https://github.com/truthwave)**  

ポートフォリオやAIツール開発に関する情報もぜひご覧ください！

## お気軽にご連絡ください
[📩 ご相談・お見積もりはこちら](mailto:realmadrid71214591@gmail.com)

---

> **「面倒な人事データ管理も、GPTでサクッと補助！」**
