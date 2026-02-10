Part-Time Manager (シフト・給料管理)

**アピールポイント:** 複雑なロジックの実装、カレンダー生成、UX向上（一括登録）

```markdown
# Part-Time Manager - 103万の壁管理ツール 💰

アルバイト学生の切実な悩みである「103万円の壁（扶養控除）」を超えないように、給料とシフトを管理するシミュレーターです。
カレンダーUIを一から実装し、直感的なシフト管理を実現しました。

**👉 [デモサイトはこちら (Demo URL)](https://kobayasiayumu.github.io/Part-Time-Manager/)**

## 💡 開発背景 (Background)
「今月いくら稼げるか」「あといくらで扶養から外れるか」を計算するのが面倒で、年末に慌ててシフト調整する友人が多くいました。
そこで、シフトを入れるだけで年収を自動計算し、危険ラインに近づくとアラートを出すツールを開発しました。

## ✨ Features (主な機能)
* **Dynamic Calendar**: JavaScriptで月ごとのカレンダーを動的に生成。月送り機能も実装。
* **Tax Alert System**: 年間の給料合計をリアルタイム集計し、103万円に対する進捗をグラフと警告メッセージで表示。
* **Bulk Entry (一括登録)**: 固定シフトの人が使いやすいよう、「毎週月・水」のように曜日指定でその月のシフトを一括登録する機能を実装しました。
* **Data Persistence**: LocalStorageにデータを保存し、リロードしてもシフト状況を保持します。

## 🛠 使用技術 (Tech Stack)
* HTML5 / CSS3 (Grid Layout)
* JavaScript (Vanilla JS)
    * `Date` Object Manipulation (Calendar Logic)
    * Bulk Insert Logic
    * LocalStorage API

## 🚀 技術的なこだわり
### 固定シフト一括登録ロジック
UX向上のため、指定した月の全日付をループし、選択された曜日（配列で管理）と一致する日のみデータを書き込むアルゴリズムを実装しました。

```javascript
// 指定月の全日付を走査し、該当する曜日にシフトを一括登録
for(let d=1; d<=daysInMonth; d++) {
    const dateObj = new Date(year, month, d);
    if(selectedDays.includes(dateObj.getDay())) {
        // データ登録処理...
    }
}
```
Author[AYUMU]
