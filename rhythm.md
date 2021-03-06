# スプリントの運営

1スプリントのやりかたを定義します。

## 前提条件

- バックログ/かんばんのツールとして、redmine_backlogsを使う前提です。
- 登場人物はプロダクトマネージャ、チームメンバ(スクラムマスター含む)です。
- gitでソースコード管理されている前提です。

## スプリントワークフロー

1. [スプリント計画ミーティング](#sprint-planning-meeting)を行います。
1. 今回のSprintでリリースするモジュールバージョンを明確にします。また、依存ライブラリ等でバージョン固定が必要なものがあれば洗い出し、固定依頼等を行います。
1. 必要に応じてSCM上でブランチを切ります。
1. [日々の作業](#daily-activities)を行います。
1. ストーリー開始時、必要に応じてフィーチャーブランチを切ります。
1. 作成したモジュールをマージし、バージョン固定/リリースを行います。
1. [スプリントレビュー](#sprint-review)を行います。

## <a name="sprint-plannning-meeting">スプリント計画ミーティング</a>

### 事前準備

1. 前々回のスプリントをクローズします。
1. 新たなスプリントを作り、クローズできなかった前ストーリーを新スプリントに移動します。
    - ストーリはただ移動させるのではなく、実態を表すストーリとして作り直してください。
    - その過程に置いて、新しいストーリが発生することもあります。
    - Ex:残った確認タスクは【Sprint○○の確認】というストーリを作り、そこに移動させるとか。

### 第1部

参加者: プロダクトマネージャ、チームメンバ

1. 新スプリントの期限をオーナに聞き入力します。
1. スクラムマスターは今回のスプリントで実施するストーリーポイントを宣言します。基本的には前回スプリントの実績と同じにします。
1. プロダクトマネージャはバックログからストーリーを選択し、スプリントバックログに入れます。
1. バックログで見積もりされていないストーリーがあればストーリーポイントの見積もりをします。
    1. プランニングポーカーカードを用意します。(最低限 0.5,1,2,3,5,8,13 のポイント分用意してください)
    1. スクラムマスターは基準ストーリーを決めます。(ストーリーポイント=5 くらいのものがよい)
    1. プロダクトマネージャがストーリーの説明をします。実装のイメージをチームメンバがハッキリと持てるまで討論してください。
    1. スクラムマスターの「せーの」の掛け声で、チームメンバは基準ストーリーと比較したストーリーポイントのカードを出します。
    1. バラついた場合は、一番大きい人、小さい人の意見を聞き、再度出しなおします。
        - バラつきが少ない場合は、スクラムマスターのひと声で決めちゃってもよいです。
    1. 大体みんなの見積もりが揃ったらバックログにストーリーポイントを記入します。
1. おつかれさまでした。

### 第2部

参加者: チームメンバ

1. 各ストーリ毎の責任者を決めます。
1. 各ストーリ毎に、仕様とチェックリストをあげます。
1. 各ストーリーに対し、スプリントレビューでデモする内容を決めます。
1. ストーリ責任者がスプリントバックログのストーリーについて、チェックリストを基に、これが全部できればストーリー完了と言えるまでタスクをあげます。(約15分)
1. タスクが出揃ったら、挙がったタスクに不備はないかを確認して、タスクに時間の見積もりを記入します。
    - タスクは必ず1日で終わるサイズにしてください。
        - ふつうのSIの現場で、経験則上5時間程度が残業なしの場合に、1理想日を現実時間に変換したものになります。
        - したがって、1つのタスクが5時間を超える場合には、タスクを分割します。
1. 時間の見積もりができない、大きく影響を与えるようなものは、時間見積もりにバッファを積むのではなく、impedimentsにタスクを上げます。
1. 見積もり合計時間を見て、スプリント内で終われせることが可能か判断します。(危なそうであれば、プロダクトマネージャと相談します。
1. おつかれさまでした。

## <a name="daily-activities">日々の作業</a>

1. [朝会](./daily_scrum.md)をします。
1. かんばんを開き、朝会で今日やると宣言したタスクを「Doing」に移します。
1. IDEを起動します。
1. 各PJをSCMから最新化します。
1. チーム内の前日のコミット内容を確認します。(気になったらコメントを入れる)
1. ペアで話し合い、分担や一緒にやるところを決め、タスクにとりかかります。
1. タスク完了したら、「Done」に移します。
1. 帰る前に「Doing」のタスクが残っていれば、作業時間・残時間を更新し「ToDo」に戻します。
    -「Doing」レーンに残したまま帰らないようにしてください。
1. おつかれさまでした

## <a name="sprint-review">スプリントレビュー</a>

参加者: プロダクトマネージャ、チームメンバ

### 事前準備

- デモを行う画面と、バックログ・かんばんを表示しておきます。
- パワポを作る場合は、カンバンとそのカンバンの説明を必ず明記します。
- KPT用にポストイット（人数*3枚程度）とボードを用意します。タイマーがあると良い。

### レビュー

1. 「それではただ今より【Sprint名】のレビュー会を開始します。」
1. ストーリー別にデモをします。
1. 「レビューを行います。何か意見があればお願いします。」
1. コードレビューを行います。
    - ここのコードレビューの意味は、実装中に気になっていたことや悩んだけどこうしてみた的なことを相談する場です。
    - ここで上がった意見は、代表者が議事録として記録します。意見が出尽くしたようなら次へ進みます。
1. 議事録を読み上げます。「【議事録担当者】さん議事録の読み上げをお願いします。」

### ふりかえり

1. 開始の挨拶をする。「それではただ今より【Sprint名】のふりかえりを開始します。」
1. KPTによるふりかえりを行います。
    1. 前回SprintのTを共有します。
    1. ちゃんとTryができたかどうか、ふりかえりをします。
    1. まずはKeepとProblemを出し合います。「KPTを行います。まずはKとPのみ出してください。時間は【５分程度】分です。」
    1. 順番にKeepとProblemを発表する。ボードにポストイットを貼ります。
        - Problem vs. us の感じを出すために、全員イスから立ち、ボードを囲むようにします。
        - この際に、他者から自分の意見と似た意見が出たら、そのポストイットに自分のポストイットも重ねて貼ります(ビンゴ的なノリ)。
        - Problemから話始めると雰囲気が暗くなるので、必ずKeepから発表してください。
    1. KeepとProblemの中で、Tryに繋げられるものを選びます。(3つ程度)
1. その他連絡事項がないか確認します。
1. おつかれさまでした。

### 事後作業

- 議事録担当者は、挙がった意見をバックログや不具合に追加します。
- プロジェクトのWikiにTryを追記します。

