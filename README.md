### VIPER学習

### VIPERとは
VIPERアーキテクチャ学習
クリーンアーキテクチャをiOS様に特化したアーキテクチャ

VIPERそれぞれのレイアーに関心がなし。
→ それぞれアクセスはProtocol経由で実施(依存性の分離)

インスタンスは外部から差し込む(依存性注入/DI)
→ テストしやすい

V View 
I Interactor インタラクた
P プレゼンタ
E エンティティ
R ルータ

UIKitのimportが推奨非推奨のところが両方ある

#### View
見た目とユーザの操作
MVCでいうViewとController？
画面変更の指示はプレゼンターからくる
UKKit使用OK

#### Interactor
ビジネスロジック(CRUD)

- 自分がやったビジネスロジックがどんなUIになってユーザに伝えるかは不明
- API通信など
- UIKit禁止

#### Presenter
ビューからのリクエストに答える
必要であればインタラクタにリクエストをする
ルータにもリクエストをする

UIKitは使用しない！！！！

MVCでいうControllerに書いていた処理(ViewとModelの司会進行みたいなイメージ)

#### Entity
データそのものを示す
ロジックは持たない

UIKitはimportしない

#### Router
画面遷移を担当
DIする
遷移先の画面を生成する

### それぞれの処理の流れ
#### View → Presenter 
ユーザの操作を依頼する
- アクションがあったことを伝えるのみで、何をやるかは興味なし
- どんな処理があるのか不明(実際にやるのは、Interactor)

#### presenter → View
Viewへの表示を指示

#### presenter → Router
一番最初の画面を生成する
→ DIをする必要がある
画面遷移を依頼する

#### presenter → Interactor
ビジネスロジックを依頼

処理した結果がInteractorから帰ってくる

#### Interactor → Entity
データを生成したり削除したり

#### そもそもDIとは
クラスAを使用するためにクラスBをインスタンス化する必要がある(密結合)
DIをする = クラスBがなくてもクラスAができるようにする
どうやって？
①クラスBのメソッド、プロパティをプロトコルを準備
②クラスAにプロトコルが型になっている変数を用意

##### 学習リソース
https://www.youtube.com/watch?v=ieqNIySokxI
https://qiita.com/REON/items/bf332ff6dbc63ee4e063
iOSアプリ設計パターン

DI
https://qiita.com/eKushida/items/78a58559aedd851d105c
