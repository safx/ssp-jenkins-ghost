
SimpleYAYAテンプレート

主にファイル数の多いテンプレートが苦手な人、てっとりばやくゴースト作りたい人、ゴースト作成経験者、自分で調べて作る気のある人向けのテンプレート。

install.txt、シェル、ゴーストのdescript.txtとdic_main.dicだけ書き換えて一発ネタゴースト作るといった使い方もできると思います。

yaya.dllはなるべく最新のものに入れ替えてください。
http://code.google.com/p/yaya-shiori/


このテンプレートには最低限のものしか書かれていませんので、以下のサイトも参考にしてください。
○FrontPage - 文Wiki「文屋」
http://emily.shillest.net/ayaya/
○文 version 5 マニュアル（AYA5のものですがYAYAもほぼ同じです）
http://umeici.hp.infoseek.co.jp/etcetera/aya5_manual/manual.html  
○CROW・SSPリファレンス
http://crow.aqrs.jp/reference/all/
○Disc-2 ゴースト制作
http://disc2.s56.xrea.com/manual/

SSPの最新機能を使いたい人はこちらが一番参考になると思います。
○SSP CHANGELOG/更新履歴 - 伺かゴースト関連。
http://ghost-dev.g.hatena.ne.jp/ponapalt/

他ゴーストの辞書を参考にする場合。
○はろーYAYAワールド
http://ms.shillest.net/yayame.xhtml
○紺野あやめ(kon'no-ayame@aya5.8)
http://umeici.hp.infoseek.co.jp/



●使用にあたって
このテンプレートを改変してゴーストを作り配布する際の使用制限は基本的にありません。
readme.txtや配布サイトにこのテンプレートの名前を書く義務、このページにリンクする義務もありません。
ただし作成したゴーストを配布する際は混乱を避けるためreadme.txt、install.txt内のゴースト名とディレクトリ名、descript.txt内の作者名、ゴースト名、各キャラクター名を必ず全て書き換えてください。



●テンプレート中身の説明

辞書について。
読み込む辞書はyaya.txtで設定さえすれば自由に辞書名を変えたりファイル数を増やしたり減らしたりできます。
（ただしyaya_shiori3.dicの中身は必ず含めて一番最初に読み込むように設定してください。動作しなくなります）
辞書の拡張子も***.dicではなく***.txtなど好きなものに変更できます。


○ghost/master/system/yaya_shiori3.dic
ゴースト「はろーYAYAワールド」のYAYAシステム辞書を一つにまとめたもの。
下のほうにSimpleYAYAテンプレート独自追加分があります。

○ghost/master/dic_main.dic
ゴーストのメインとなる部分。「メインキャラの名前」は作成するゴーストのsakura.nameに置き換えてください。
「トランスレート」「選択肢」「起動・終了」「交代」「複数起動関係イベント」「消滅」「ランダムトーク」「マウス反応」「キー反応」「最小化」「時間経過イベント」「シェル変更」「メニュー定義等のリソース系」
（省略可）と書かれてるものは削除しても構いません。（イベントは無反応になるか、他のイベントが代替します。リソースはデフォルトのものになります）

○ghost/master/dic_utility.dic
機能系イベント
「インストール」「メールチェック」「ネットワーク更新」「ヘッドラインセンス」「RSS」「ファイル作成」「時計合わせ」「URLドロップ」「ファイルドロップ」
トークがシステムメッセージ風に書かれているためこのまま改変せずに使ってもそんなに違和感ないと思います。
この辞書を削除しても一応ゴーストとして成立しますが、ベースウェアによってはイベントを記述しないと実行できない機能もあるため記述した方が親切です。

○tool/
YAYAデバッグツール、辞書暗号化ツールが入ってます。（AYA用ですがYAYAでも使用できます）
開発時にしか使わないものなのでゴーストを配布する時は含める必要はありません。

○shell/master/
簡易シェル、オーナードローメニュー画像が入ってます。
そのまま、もしくは改変して自作ゴーストに使っても構いません。



●注意

このテンプレートでは選択肢やアンカーを
\q[選択肢名,ジャンプ先イベント名]
といきなり独立した関数で書きます。

ブラウザでURLを開く時は
\q[選択肢名,http://...../]
と直接URLを書きます。これはベースウェアの仕様であり変更できません。
アンカーもURLでブラウザオープンするよう設定していますが変更可能です。
この動作法を変えたい場合はdic_main.dic内の選択肢処理を書き換えてください。

reference[0]はreference0と書けないようになっています。
書けるようにしたい方はyaya_shiori3.dicの上のほうにある設定を変更してください。

ゴーストリスト取得したい、自動で\0x01をカンマ変換させたい場合もyaya_shiori3.dicの設定を書き変えてください。
ランダムトーク頻度(aitalkinterval)初期値もここで変更できます。



●テンプレート独自関数、変数について

文Wikiのこのページに掲載されています。
便利なものが多いので参考にしてみてください。
http://emily.shillest.net/ayaya/index.php?%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0%E8%BE%9E%E6%9B%B8%2Fyaya_shiori3.dic
http://emily.shillest.net/ayaya/index.php?%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0%E8%BE%9E%E6%9B%B8%2Fyaya_optional.dic
以下載ってないもののみ説明します。

○関数

AYATEMPLATE.EscapeText
第一引数 エスケープしたいテキスト
>さくらスクリプトの中に「]」など記述した時タグが崩れるのを防ぐための関数


○変数

weekj
>現在曜日を漢字一文字で表示。
>ただ曜日を表示するだけならweekdayではなくこちらを。


○関数名の省略

SHIORI3FW.EscapeAllTags、SHIORI3FW.EscapeDangerousTags、SHIORI3FW.IsGhostExist、SHIORI3FW.RefreshFMOTable、SHIORI3FW.FMOCache、SHIORI3FW.SetDelayEventは「SHIORI3FW.」を省略して書けます。
AYATEMPLATE.EscapeTextは「EscapeText」と書けます。


○更新履歴
2009/03/28  ・readme.txt「テンプレート独自関数、変数」、yaya_shiori3.dicSimpleYAYAテンプレート独自追加分修正
2009/03/22  ・OnChoiceSelect, OnChoiceSelectEx, 
              OnAnchorSelect, OnAnchorSelectEx を厳密な記述に修正
