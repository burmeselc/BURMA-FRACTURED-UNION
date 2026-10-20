# BURMA 1948 — Prototype v1.5

ブラウザ試作（1948年1月〜12月）。統一主体台帳・州制度審議・地方政治AI。

## 起動

[`index.html`](../index.html) をChromium等で開く。単一HTMLで動作し、外部通信不要。ブラウザ内保存とJSONでの移送に対応。

## データ

`burma_1948_entity_catalog_v15.json` は、v1.5のJavaScriptから抽出した読み取り用の主体・関係一覧である。現時点のゲームはこのJSONファイルを**直接読み込まない**。追加変更をゲームに反映するにはHTML内の台帳定義の更新が必要。次版でデータとエンジンの物理的な分離を計画する。

- `entity.id` 安定識別子。`type` は political_organization, military_organization, administration, social_group, person, territory を区別。
- `status` は historical（歴史組織）、institution（制度上の役割）、model（分析用集約）、hypothetical（プレイ中生成）を区別。
- `relations` に所属・職務・統治地域などの**関係の種別**を記録。`initial_simulation_edges` はゲーム用の協力度・競合値であり史実の推計ではない。
- `institutions` は州別の制度区分、`proposals` は州内事項と連邦事項の区別。

## 主な実装

- v1.4までの政策選択、勢力AI、全国14地域、シャン州12地域、政治ネットワークは継承。
- 59件の主体、43本の関連線（初期値）。社会集団と史実の政治組織を区別するための台帳検索・詳細表示を追加。
- シャン、カチン、カレンニー、チンの州政治・諮問手続を模した制度協議。チンは州議会と同一扱いにしない。
- 統計、議席数、政治勢力の支持基盤などの数値は、断りがない限り試験用の仮定値。

## 出典入口と歴史的注意

- 1947年憲法第92条、154条以下（州の立法権・シャン州評議会）：https://www.blc-burma.org/q-my/book/export/html/115/
- 1948年独立期：英国National Army Museum https://www.nam.ac.uk/explore/timeline-burma-army
- KNU公式歴史叙述（当事者史料）：https://www.knuhq.org/about-us/history

1948年の州権限を抽象化したゲームであり、史実の議決数や政治選択の予測ではない。史料確度の低い項目は今後校閲する。

## 検証

Chromiumヘッドレス環境で、初期化、59主体表示、検索、州制度議案、12か月進行、JSONインポート・エクスポート、旧保存形式の一部読替、390px幅の横はみ出し、JavaScriptの構文を検査。iPhone実機での検査は未実施。

## 次の優先項目

1. v1.6: 主体台帳を実コードの単一の情報源へ移行し、史実と架空史の組織系譜を整理。
2. v1.7: プレイヤー操作主体の切替（連邦政府、KNU、CPB、シャン政治主体）。
3. v1.8: 指導者・派閥・議会手続、組織間の提案・拒否と後継関係。
4. v2: 地域別の人口・階層・経済計算と財政を整合的に統合。