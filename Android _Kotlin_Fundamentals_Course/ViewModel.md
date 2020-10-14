# ViewModelについて

参考記事 https://codelabs.developers.google.com/codelabs/kotlin-android-training-view-model/index.html?index=..%2F..android-kotlin-fundamentals#0

- Androidアプリのアーキテクチャガイドラインでは、異なる処理を持つクラスを分離することを推奨している。
- UIコントローラは、基本的にはActivityか、Fragmentを指す。
  - UIコントローラーでは、UIとユーザー操作の相互作用を処理するロジックのみを書く。
  - UI部分に表示するデータを含めるべきではない。データを保存して管理する役割としてViewModelが存在している。
- ViewModelはAndroidアーキテクチャコンポーネントの1つ。
- ViewModelクラスは、UI関連のデータを保存および管理をする。
  - ViewModelクラスがあると、データは画面の回転などのViewが再構成される際にデータが新規に生成されることなく、ユーザーが操作した続きから操作することができる。
- ViewModelProvider.FactoryViewModelは、引数のViewModelクラスのインスタンスを生成するためのFactory。

次の表は、UIコントローラーとViewModelの位置付けを比較する。

|UIコントローラー|ViewModel|
|:--|:--|
|ScoreFragmentなどのActiviryやFragmentのこと。 | ScoreViewModelなど。|
| UIに表示される部分のみで、データ部分は保持しない。| UIコントローラーがUIに表示するためのデータを保持する。|
| ViewModelにあるデータを表示するためのコードと、クリックリスナーなどのユーザーイベント。 | データ処理用のコード。|
|Androidを横にするなど、画面が変更されるたびに破棄され、再作成される。| 関連付けられたUIコントローラーが完全に消えた場合にのみ破棄される。アクティビティの場合は、アクティビティが終了したタイミング。フラグメントの場合は、フラグメントがデタッチされたタイミング。|
| Viewを持っている。| Activity、Fragmentなど、Viewの処理を書くことはできない。データに関して、Viewは画面の変更時に破棄されてしまうが、ViewModelは破棄されない。|
|関連するViewModelを参照している。| 関連するUIコントローラーを参照していない。|
