# v1.6 基礎データとゲームの関係

唯一の編集対象は \`data/1948/catalog.json\`。 \`python tools/build_catalog.py\` を実行すると、GitHub Pagesが読み込む \`data/1948/catalog.generated.js\` と、単一ファイルのオフライン版 \`dist/burma_1948_standalone_v16.html\` が再生成されます。

\`entities\` は政治・軍事組織、行政機構、人物、社会集団、地域を安定IDで管理。 \`status\` の historical / institution / model / hypothetical を区別します。 \`relations\` は型付きの基礎関係31件、 \`initial_simulation_edges\` は協力・競合のゲーム用仮定値12件です。 \`geographies\` は全国14分析地域・シャン州12地点・域内政治主体16件、 \`institutions\` は州の制度、 \`proposals\` は政策審議、 \`sources\` は典拠入口を管理します。

\`lineage\` は史料で確認された組織系譜を後日登録するための欄（現在空欄）です。ゲーム中の架空の分裂は \`splits[]\` の状態と \`dynamic:\` IDで管理し、史実の組織系譜と混同しません。1948年当時存在しない後年の組織を自動配置しません。

今版は台帳・地域・初期ネットワーク・制度定義を外部化したものです。政策効果や旧来の勢力AIを完全にデータ駆動に移したわけではありません。初期の勢力支持・経済・政治関係の数値は史実の測定値ではありません。行政境界図も模式図です。

テストはChromiumで1280px・390pxの表示、主体検索、チン特別区の制度審議、12か月進行、保存・復元と主体グラフ書出を確認しました。開発環境のファイルURL制限により、検証は同じ生成カタログをページに埋め込んで実施。Pagesのライブ通信・iPhone実機は未検証です。
