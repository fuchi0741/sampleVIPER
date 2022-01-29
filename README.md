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

#### View
見た目とユーザの操作
MVCでいうViewとController？
画面変更の指示はプレゼンターからくる

#### Interactor
ビジネスロジック(CRUD)

#### Presenter
ビューからのリクエストに答える
必要であればインタラクタにリクエストをする
ルータにもリクエストをする

#### Entity
データそのものを示す
ロジックは持たない

#### Router
画面遷移を担当
DIする
遷移先の画面を生成する

### それぞれの処理の流れ




##### 学習リソース
https://www.youtube.com/watch?v=ieqNIySokxI
