# Part-Time Manager - 103万の壁管理ツール 💰

アルバイト学生の切実な悩みである「103万円の壁（扶養控除）」を超えないように、給料とシフトを管理するシミュレーターです。
カレンダーUIを一から実装し、直感的な操作で年収管理ができます。

**👉 [デモサイトはこちら (Demo URL)](https://kobayasiayumu.github.io/Part-Time-Manager/)**

## 💡 開発背景 (Background)
「今月いくら稼げるか」「あといくらで扶養から外れるか」を計算するのが面倒で、年末に慌ててシフト調整する友人が多くいました。
そこで、シフトを入れるだけで年収を自動計算し、危険ラインに近づくとアラートを出すツールを開発しました。

## ✨ Features (主な機能)

* **Dynamic Calendar**: JavaScriptで月ごとのカレンダーを動的に生成。月送り機能も実装。
* **Tax Alert System**: 年間の給料合計をリアルタイム集計し、103万円に対する進捗をグラフと警告メッセージで表示します。
* **Bulk Entry (一括登録)**: 「毎週月・水」のような固定シフトの人が使いやすいよう、**指定した月の特定曜日にシフトを一括登録する機能**を搭載しました。
* **Data Persistence**: LocalStorageにデータを保存し、リロードしてもシフト状況を保持します。

## 🛠 使用技術 (Tech Stack)

* HTML5
* CSS3 (Grid Layout, Flexbox)
* JavaScript (Vanilla JS)
    * `Date` Object Manipulation (Calendar Logic)
    * Bulk Insert Algorithm
    * LocalStorage API

## 🚀 技術的なこだわり

### 1. 固定シフト一括登録ロジック
UX（ユーザー体験）を向上させるため、ユーザーが選択した曜日（例：月・水）に基づいて、表示中の月の該当する日付全てにデータを書き込むアルゴリズムを実装しました。

```javascript
// 指定月の全日付を走査し、該当する曜日にシフトを一括登録
for(let d=1; d<=daysInMonth; d++) {
    const dateObj = new Date(year, month, d);
    const dayOfWeek = dateObj.getDay(); // 0(Sun) - 6(Sat)

    // 選択された曜日リストに含まれていれば登録
    if(selectedDays.includes(dayOfWeek)) {
        const dateStr = ...; // 日付文字列生成
        shifts[dateStr] = { rate, hours };
    }
}
