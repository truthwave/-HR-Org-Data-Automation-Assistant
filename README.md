# 人事・部署・役職データ処理アシスタント

> **台帳整備：60分 → 8分。**
> 役職チェック：手作業 → 自動。
> 人事は、判断だけに集中する。

<p align="center">
<img width="1536" height="1024" alt="人事" src="https://github.com/user-attachments/assets/5b6c8b59-7aad-4a82-82ff-caddf98089b0" />
</p>

👉[ ChatGPTで今すぐ試す](https://chatgpt.com/g/g-686cbd4b28c881918e461fb62a7e3c32-ren-shi-bu-shu-yi-zhi-tetachu-li-asisutanto)

---

## 体験（3つで終わる）
- **整形**：CSV/カラム設計・コード体系を自動提案（社員番号／部署コード／役職コード 等）
- **検証**：部長=部署1名・課長=課1名など**制約ロジック**を生成（MUMPS／SQL／Python）
- **統合**：重複検出・マスタ突合・差分レポートを**表／JSON／手順書**で出力

---

## Before → After

- 台帳整備：60分 → 8分
- 役職ルールチェック：0分（自動）
- 重複統合の初動：半日 → 20分
> ※ 目安。環境・データ品質により変動します。

---

## 使用例（短文）

**役職制限ロジック（MUMPS の骨格）**
前提：役職インデックス ^EMPIDX("ROLE",dept,sec,title,empId) がある想定。

> ; 1=許可 / 0=不可
> CHKROLE(DEPT,SEC,TITLE)
>   NEW CNT,ID SET CNT=0,ID=""
>   FOR  SET ID=$ORDER(^EMPIDX("ROLE",DEPT,SEC,TITLE,ID)) Q:ID=""  SET CNT=CNT+1
>   QUIT $SELECT(TITLE="部長":CNT<1, TITLE="副部長":CNT<1, TITLE="課長":CNT<1, TITLE="課長代理":CNT<1, 1:1)

**CSV レイアウト（最小）**
| 項目           | 型      | 必須  | 例       |
| ------------ | ------ | --- | ------- |
| employee_id  | string | Yes | E000123 |
| dept_code    | string | Yes | D120    |
| section_code | string | No  | S07     |
| title_code   | string | Yes | MGR     |
| full_name    | string | Yes | 山田 太郎   |

---

## 使い方（3ステップ）
1.現状の**列名／コード表／業務ルール**を貼る<br>
2.目標状態（**一意制約／役職上限／命名規則**）を伝える<br>
3.生成された**設計・ロジック・検証手順**で即実装／検証

---

## 📸 **体験イメージ・資料**
![デモ動画](https://github.com/truthwave/-HR-Org-Data-Automation-Assistant/blob/main/%E8%B3%87%E6%96%99/%E3%83%87%E3%83%A2%E5%8B%95%E7%94%BB.gif)

### [スクリーンショットはこちら](https://github.com/truthwave/-HR-Org-Data-Automation-Assistant/tree/main/%E8%B3%87%E6%96%99/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88)

---

## 技術メモ

- **プロンプト設計**：人事ルールを正規化し、制約→検証→例外処理の順で出力
- **MUMPS対応**：インデックス設計を前提に**件数判定／一意制約**の併用を推奨
- **セキュリティ**：実データは入力せず、**架空データ**で検証

---

## 注意

- 実在の**個人情報**は入力しないでください
- 生成物は**参考**です。導入は専門家レビューで
 
---

## 🧑‍💻 作者

**[Truth Wave ― 真理の波](https://github.com/truthwave)**  

ポートフォリオやAIツール開発に関する情報もぜひご覧ください！

## お気軽にご連絡ください
[📩 ご相談・お見積もりはこちら](mailto:realmadrid71214591@gmail.com)

---

> **飾るな。制約と結果だけを残せ。**
