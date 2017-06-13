---
title: SQL Server Management Studio - Changelog (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 470e6c83318eaf8eb579d053f65b5353862eb4c7
ms.openlocfilehash: 23e304e52967d5d16672872d8d5712f26ef8c610
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017

---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)

## <a name="ssms-171-release"></a>SSMS 17.1 リリース
一般的に使用できる |ビルド番号: 14.0.17119.0

### <a name="enhancements"></a>機能強化

- プロファイラー: ヘルプ > 約リリース バージョン番号 (例: 17.1) が表示されます
- 分析サービスのユーザーが 1200 のデータ ソースの資格情報を更新できます TM モデル以降、データ ソースのコンテキスト メニューから
- 組み込みの SSIS レポート CTP 2.1 で SSIS のスケール アウトが実行からログを表示するようになりました
- SSIS のスケール アウトの管理アプリケーション
  - スケール アウト マスターに関する基本的な情報を表示します。
  - スケール アウト配置にワーカーが簡単に追加します。
  - すべてのスケール アウト ワーカーとそれらに関する基本的な情報を表示およびことができますも有効または無効にして簡単にします。

### <a name="bug-fixes"></a>バグの修正
- Always On:
  - ここで、可用性レプリカのプロパティが常に表示されます「自動フェールオーバー」モードと WSFC Ag の問題を修正しました。
  - 読み取り専用ルーティング リストが、可用性グループを更新するときに上書きされた問題を修正しました
- Always Encrypted: 問題を修正、DacFx によって生成される情報を生成されたログ ファイルがありませんでした。
- ここで、UI が常に実際結合型の属性の表示アダプティブ非結合演算子問題では ShowPlan: 修正。
- セットアップの実行:
  - ここで SSMS 17.0 が重大な SSDT Visual Studio 2013 [項目 3133479 の接続] で問題を修正しました
  - ここでセットアップの最後に"Restart"をクリックしてがないコンピューターの再起動問題を修正しました
- スクリプト: 一時的に妨げ SSMS そのオプションを無効にして削除スクリプトを作成しようとするときに、Azure のデータベース オブジェクトを誤って削除します。  適切な修正プログラムは、SSMS の今後のリリースになります。
- オブジェクト エクスプ ローラー: は、「データベース」ノードは展開されませんでした「AS コピー」を使用して作成された Azure データベースへの接続時に、問題を修正

## <a name="ssms-170-release"></a>SSMS 17.0 リリース
一般的に使用できる |ビルド番号: 14.0.17099.0

### <a name="enhancements"></a>機能強化 

- アップグレード パッケージと Windows Software Update Services (WSUS) 
    - 17.X の将来のリリースは、小型の累積更新プログラム パッケージを含める 
  - 更新プログラム パッケージは、WSUS カタログにもパブリッシュします。  
- アイコンの更新
    - VS Shell の指定されたアイコンと一致して、高 DPI の解像度をサポートするアイコンが更新されました
    - 16.X バージョンと 17.X バージョンを区別する新しい SSMS とプロファイラー プログラムのアイコンに更新します。
- SQL PowerShell モジュール
  - SQL Server PowerShell モジュールは、SSMS から削除され、今すぐ (PowerShell 5.0 はモジュールのバージョン管理をサポートするために今すぐ必要な)、PowerShell ギャラリーを介しては付属しています
  - 「プレゼンテーション」(書式) (データベースなどに表示、サイズ、使用可能な領域およびテーブル表示行カウントと領域使用状況) 一部の SMO オブジェクトの他の機能強化
  - OE の [PowerShell の開始] メニューから、PowerShell コマンド プロンプトが呼び出されたときに追加の色づけ
  - AG コマンドレットに (New-SqlAvailabilityGroup、Join-SqlAvailabilityGroup、および Set-SqlAvailabilityGroup) に -ClusterType パラメーターと -RequiredCopiesToCommit パラメーターを追加しました。
  - Add-SqlAzureAuthenticationContext コマンドレットに -ActiveDirectoryAuthority パラメーターと -AzureKeyVaultResourceId パラメーターを追加しました。
  - 追加した Revoke SqlAvailabilityGroupCreateAnyDatabase、Grant SqlAvailabilityGroupCreateAnyDatabase およびセット SqlAvailabilityReplicaRoleToSecondary コマンドレット
  - Set-sqlavailabilityreplica および New-sqlavailabilityreplica コマンドレットに追加する-SeedingMode パラメーター
  - Get-sql データベースに追加された-connectionstring パラメーター
- SQL Server on Linux
    - ログ配布に対する一般的な機能強化と修正を行いました。
  - ネイティブの Linux パス アタッチのサポートを追加、バックアップの復元とデータベース
  - 監査ログのコピー先フォルダーのネイティブの Linux パスのサポートが追加されました
- Analysis Services
  - DAX クエリ ウィンドウに保存します。
    - エディターでは、照合するかっこ
    - メジャーの定義と定義 VAR 構文でサポート
    - さまざまな Intellisense の機能強化
  - ユニバーサル認証
    - ユーザー名とパスワードのない Azure ログイン ダイアログ ボックスは、接続を処理するを指定することができます。
  - SSMS PQ 統合: 
    - 構造化されたデータ ソースが機能のスクリプト作成 
    - 表示と PQ UI で構造化されたデータ ソースの編集
- 新しい [一意制約の追加] テンプレート
- Showplan
    - プロパティ ウィンドウにスレッド全体の経過時間の合計ではなく最大値を表示します。
    - 新しい mem grant 演算子のプロパティを公開します。
    - ライブ クエリ統計の [クエリの編集] ボタンが有効になりました。
    - インターリーブ実行のサポート
  - 「分析実際の実行プラン」に新しいオプション
  - プラン表示の比較対象に全般的改良点
  - 一致するノードの 2 つのクエリ プランの基数の推定で重要な違いを検索し、可能性のある根本的原因の基本的な分析を実行する Showplan 比較の機能で機能が導入されました
- 登録済みサーバー エクスプローラーから Configuration Manager を削除しました。
- Azure Blob ストレージから監査ログを読み取り可能
- Always Encrypted にパラメーター化機能が追加されました。詳細については、[このページ](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/)を参照してください。 
- Azure SQL DB への AAD ユニバーサル認証接続でカスタム テナント ID がサポートされるようになりました。 
- Azure SQL Database のスクリプト生成で、テキスト、ルール、およびデータベースが完全にスクリプト化されるようになりました。
- スプラッシュ スクリーンでの SSMS と Profiler のブランド化が修正されました。
- SSMS からユーティリティ コントロール ポイントの UI が削除されました。
- SSMS"PremiumRS"エディションの SQL Azure データベースを作成できます。
- Always On 可用性グループ
  - 新しいクラスターの種類のサポートを追加します外部および NONE。
    - Linux 上の SQL Server のサポートを追加します。
    - 初期データ同期のためのオプションとして、自動シード処理を追加します。
    - エンドポイント URL の処理、DB の更新と UI のレイアウトなど、いくつかの欠陥を固定
    - 削除された Azure のレプリカに関連する機能
  - いくつかの可用性グループ キーワードに対する IntelliSense サポート強化
- 利用状況モニター
  - SSMS の出力ウィンドウに新しい「利用状況モニター」ウィンドウを追加
  - ポップアップ メッセージではなく、ウィンドウの出力に情報を記録する接続/タイムアウト エラー メッセージの変更
  - 削除された空グラフの [概要] セクション (5 日グラフ)
  - 「(一時停止)」に追加の概要のタイトルの利用状況モニターのデータ収集が一時停止した場合
  - グラフ [テーブル] フォルダーの下にある SQL Server - 新しいアイコン ノードとエッジ テーブルのグラフ - グラフのノードとエッジ テーブルへの graph の拡張機能が表示されます - テンプレートで作成するグラフで使用できるノードとエッジ テーブル
- プレゼンテーション モード
    - クイック起動 (Ctr+Q) で 3 つの新しいタスクを使用できます。
    - PresentOn: プレゼンテーション モードをオンにします。
    - PresentEdit: プレゼンテーション モードでのプレゼンテーションのフォント サイズを編集します。  クエリ エディター用の "テキスト エディター フォント"。  その他のコンポーネント用の "環境フォント"。
    - RestoreDefaultFonts: 既定の設定に戻ります。
    - *注: 現時点では、PresentOff コマンドは存在しません。プレゼンテーション モードをオフにするには、RestoreDefaultFonts を使用します。*

### <a name="bug-fixes"></a>バグの修正

- プラン表示は surfacebook タッチパッド経由でスクロールするときに SSMS がクラッシュした問題を修正しました
- 長整数型の SSMS がハングする問題を修正しましたが、復元またはオフラインにされているデータベースのプロパティを取得中に時間 
- ここで「ヘルプ ビューアー」開けませんでした RC のビルドで問題を修正しました
- SSMS でない可能性があります「メンテナンス プランのタスク ツールボックス」アイテムをここで問題を修正しました。
- SSMS のユーザーがデータベースの名前に中かっこが含まれている場合は、データベースを圧縮することで問題を修正しました。 [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3122618)を参照)。
- 問題を修正、削除するスクリプト SSMS がしようとして、Azure のデータベースが実際の原因と、データベース自体の削除。 [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3131458/)を参照)。
- ユーザー定義テーブル型で既定値がスクリプト化されない問題を修正しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3119027)を参照)。
- インデックスのコンテキスト メニューに関するパフォーマンスの改善を再度実行しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3120783)を参照)。
- 実行プランで欠落インデックスの上にマウスを置いたときに過剰なちらつきを発生させる問題を修正しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3118510)を参照)。
- スクリプト作成時に SSMS の DB オフラインがオンラインになる問題を修正しました ([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3118550)を参照)。
- SSMS のローカライズされた (英語以外の) バージョンで、さまざまな UI の修正を実行しました。
- SQL 2016 SP1 Standard Edition をターゲットとした場合に [Always Encrypted キー] ノードが欠落する問題を修正しました。
- Always Encrypted
    - SQL 2016 RTM Standard Edition または SQL 2014 (またはそれより前) のサーバーをターゲットとした場合に、[常に暗号化] メニューが間違って有効化されていました。
    - CREATE または ALTER 構文を使用すると、IntelliSense でエラーが報告される問題を修正しました。
    - CMK/CEK にエスケープする必要がある (角かっこで囲まれた) 文字が含まれていた場合、暗号化が失敗する問題を修正しました。
    - SSMS でメモリ不足例外が発生すると、代わりにネイティブ (64 ビット) の PowerShell を使用することを提案するエラーがユーザーに表示されます。
    - ユーザーが従来の Azure サブスクリプションではなく Resource Group Manager サブスクリプションを使用した場合に AE ウィザードが失敗する問題を修正しました。
    - ユーザーがいずれのサブスクリプションにもアクセス許可がないか Azure Key Vault を持っていない場合に、AE ウィザードに適切でないエラーが表示される問題を修正しました。
    - 複数の AAD があるときに Azure Key Vault のサインイン ページに Azure サブスクリプションが表示されないという AE ウィザードの問題を修正しました。
    - Azure Key Vault のサインイン ページに、ユーザーが閲覧者アクセス許可を持っている Azure サブスクリプションが表示されないという AE ウィザードの問題を修正しました。
  - ここでリソース ファイルが正しく読み込めません問題を修正しました、不正確なエラー メッセージのため、
- SSMS の [セットアップ] ページ上のハイパーリンクのコントラストを改善しました。
- SQL Server Express (2016 SP1) に接続したときに Polybase ノードが表示されない問題を修正しました。
- SSMS がある v140 に Azure DB の互換性レベルを変更することではない問題を修正しました
- Azure データベースの一覧を展開するときのオブジェクト エクスプローラーのパフォーマンスを強化しました ([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3100675)を参照)。
- リレーショナル サーバー以外の種類のサーバー (AS\RS\IS) で [SQL Server ログの表示] コンテキスト メニュー項目が間違って表示される問題を修正しました。 
- SQL 認証を使用する Analysis Services のパーティション クエリの構文チェックで、ログイン失敗メッセージが表示される問題を修正しました。
- SSMS で、プレビュー 1400 コンパクト レベルの AS 表形式モデルの名前を変更するとエラーが発生する問題を修正しました。
- まれな状況で、AS サーバー上で無効な操作を試行した後で発生する可能性がある "モデルの操作に失敗する" 問題を修正しました。モデルの保存に失敗した後、ローカルの変更は元に戻ります。
- Analysis Services 同期データベースのポップアップ ダイアログの文字の間違いを修正しました。
- コンテナーのバックアップ/復元ダイアログが、複数のモニター セットアップで画面の表示領域を超えて表示される。 
- 対象オブジェクトの名前に "]" が含まれている場合、SecurityPolicy を作成できない。
- SSMS 2016 の [最近使用した項目を開く] メニューに、最近保存したファイルが表示されない ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)を参照)。
- VS Shell の更新時のユーザー設定のリセットが削除されました。
- ある問題が修正されたため、ユーザーが SQL Server 2017 上のデータベースの互換性レベルを変更することができません。
- AAD ユニバーサル認証を使用するクエリ ウィンドウで、1 時間後にクエリを更新できなくなる。
- SSMS からユーティリティ コントロール ポイントの UI が削除されました。
- トークンの初期の有効期限が切れると、AD ユニバーサル認証接続でデータを照会できない。
- Azure SQL DB 間のルールをスクリプト化できない。
- SQL PowerShell が以前の SQL インスタンス (2014 以前) に接続できないという問題が修正されました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)を参照)。
- 登録済みサーバーのインポートに失敗すると SSMS がクラッシュする原因となる問題が修正されました。
- ユーザーにデータベースに対する特定のアクセス許可がある場合に SSMS がクラッシュする原因となる問題が修正されました。 
- SSMS - ビューの確認時にデザイン画面にテーブルが表示されなくなる ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views)を参照)。 
- テーブルのスクロール バーでテーブルの内容をスクロールできない。上下の方向キーでのみスクロールできる。 バグがあるスクロール バーを使用してスクロールを試した後でテーブルの内容をスクロールできる場合もある ( [Connect アイテム](
http://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view)を参照)。 
- ルート ノードを更新した後、登録済みサーバーにアイコンが表示されない。
- Azure v12 サーバーで [データベースの作成] のスクリプト ボタンを使用してスクリプトを実行すると、"スクリプトを作成するアクションはありません" というメッセージが表示される。
- SSMS の [サーバーに接続] ダイアログで、新しい接続ごとの [追加のプロパティ] タブがクリアされない。
- タスクの生成スクリプトで、Azure SQL DB のデータベースの生成スクリプトが生成されない。
- ビュー デザイナーのスクロール バーが無効になっているように表示される。
- Always Encrypted AVK キーのパスにバージョン ID が含まれていない。
- クエリ ウィンドウ内のエンジン エディション クエリの数が削減されました ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3113387)を参照)。
- 暗号化が正しく処理されていない状態でモジュールを更新すると、Always Encrypted でエラーが発生する。
- OLTP と OLAP の既定の接続タイムアウト値が 15 秒から 30 秒に変更され、無視された接続エラーのクラスが修正されました。 
- カスタム レポートの起動時の SSMS のクラッシュが修正されました ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3118856)を参照)。
- Azure SQL データベースで [スクリプトの生成] が 実行できないという問題が修正されました。
- [スクリプト化] と [スクリプトの生成] ウィザードが修正され、ストアド プロシージャなどのオブジェクトのスクリプト化の際に余分な改行が追加されないようになります ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3115850)を参照)。
- SQLAS PowerShell プロバイダー: Dimension フォルダーと MeasureGroup フォルダーに LastProcessed プロパティが追加されます ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3111879)を参照)。
- ライブ クエリ統計: バッチの最初のクエリしか表示されないという問題が修正されました ( [項目の接続](http://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- プラン表示: プロパティ ウィンドウにスレッド全体の合計ではなく、最大値が表示される。
- クエリ ストア: 豊富な実行バリエーションの新しいレポートがクエリに追加される。
- オブジェクト エクスプローラーのパフォーマンスの問題 ([Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3114074)を参照):
    - テーブルのコンテキスト メニューがすぐにハングする。
    - テーブルのインデックスを右クリックすると SSMS の動作が遅くなる (リモート (インターネット) 接続経由の場合)。 
    - サーバーでのテーブルの並べ替えクエリの発行を避ける。
- SSMS から (Azure VM にデータベースを展開するための) Azure 展開ウィザードが削除されました。
- SSMS の実行プランに不足しているインデックスが表示されないという問題が修正されました ([Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3114194)を参照)。
- SSMS での一般的なシャットダウン時のクラッシュの問題が修正されました。
- オブジェクト エクスプローラーで、PolyBase|スケールアウト グループ ノードのコンテキスト メニューを表示したときにエラーが発生する問題が修正されました ([Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3115128)を参照)。
- データベースに対するアクセス許可を表示しようとすると SSMS がクラッシュする場合があるという問題が修正されました。
- クエリ ストア: クエリ ストア レポートの結果グリッドのコンテキスト メニュー項目が全体的に改善されました。
- 関連付けられていないオブジェクトで既存のテーブルに対して Always Encrypted を構成すると、エラーが発生して実行できない ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3103181)を参照)。
- 複数のスキーマを持つ既存のデータベースに対して Always Encrypted を構成できない ( [項目の接続](http://connect.microsoft.com/SQLServer/feedback/details/3109591)
- データベースにシステム ビューを参照するビューが含まれているため、Always Encrypted の暗号化された列ウィザードでエラーが発生する ( [項目の接続](http://connect.microsoft.com/SQLServer/feedback/details/3111925)
- Always Encrypted を使用して暗号化する場合、暗号化が正しく処理されていない状態でモジュールを更新するとエラーが発生する。
- [新規サーバーの登録] ダイアログで UI が切り捨てられる問題が修正されました。
- 引用符で囲まれた文字列定数値を含む式が DMF 条件 UI で正しく更新されない問題が修正されます。
- カスタム レポートの実行時に SSMS がクラッシュする原因と思われる問題が修正されました。
- [Scale Out で実行] メニュー項目が フォルダー ノードに追加されます。
- Azure SQL DB ファイアウォール ホワイト リスト IP アドレスの機能を問題を修正しました。
- Ssms のオブジェクト参照の原因となった問題設定されていない例外のソースとして多次元パーティションの編集時に固定
- Ssms のオブジェクト参照の原因となった問題設定されていない例外多次元 AS から顧客アセンブリを削除するときに固定サーバー
- 問題が修正されました AS 表形式 1400 db 名の変更が失敗しました
- 接続プロパティ ダイアログ ボックスから表形式データソースとして 1400 compat レベルをスクリプトに問題を修正しました。
- 前提として 1400 compat レベルのモデル内のテーブルがある、少なくとも 1 つのパーティションを削除します。
- Ctrl キーを押し、R は今すぐ SSMS DAX クエリ エディターでの結果ウィンドウを切り替えます


## <a name="ssms-1653-release"></a>SSMS 16.5.3 リリース
一般公開 | ビルド番号: 13.0.16106.4

このリリースでは次の問題が修正されました。

* SSMS 16.5.2 で、テーブルに複数のスパース列がある場合に 'Table' ノードが拡張される原因となっていた問題が修正されました。

* ユーザーは、SSIS カタログに、Microsoft Dynamics AX/CRM Online のリソースに接続される OData 接続マネージャーを含む SSIS パッケージを展開できます。 詳細については、「[OData 接続マネージャー](https://msdn.microsoft.com/library/dn584133.aspx)」を参照してください。

* 関連付けられていないオブジェクトで既存のテーブルに対して Always Encrypted を構成すると、エラーが発生して実行できない ( [Connect ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects) を参照)。

* 複数のスキーマを持つ既存のデータベースに対して Always Encrypted を構成できない ( [Connect ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work) を参照)。

* データベースにシステム ビューを参照するビューが含まれているため、Always Encrypted の暗号化された列ウィザードでエラーが発生する ( [Connect ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors) を参照)。

* Always Encrypted を使用して暗号化する場合、暗号化が正しく処理されていない状態でモジュールを更新するとエラーが発生する。

* *[最近使用した項目を開く]* メニューに、最近保存したファイルが表示されない ( [Connect ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files) を参照)。

* テーブルのインデックスを右クリックすると SSMS の動作が遅くなる (リモート (インターネット) 接続経由の場合)。 [Connect ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection) を参照)。
 
* SQL デザイナーのスクロール バーの問題が修正されました ( [Connect ID 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016) を参照)。

* テーブルのコンテキスト メニューがすぐにハングする。 
 
* SSMS で利用状況モニターの例外がスローされ、クラッシュする場合がある ( [Connect ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/) を参照)。

* ".NET ランタイムの内部エラーにより、処理が中止されました。IP 71AF8579 (71AE0000)、終了コード 80131506" という内容のエラーで SSMS 2016 がクラッシュする。


## <a name="ssms-1651-release"></a>SSMS 16.5.1 リリース
一般公開 | ビルド番号: 13.0.16100.1

* 制約の確認時に Invoke-Sqlcmd で誤って複数の行が挿入されるという問題を修正しました。 [Microsoft Connect アイテム: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

* 可用性グループの作成時に ENU 以外の言語バージョンが完全に動作しないという問題を修正しました。

* クエリ プラン XML をクリックしたときに適切な SSMS UI が開かないという問題を修正しました。


## <a name="ssms-165-release"></a>SSMS 16.5 リリース
一般公開 | ビルド番号: 13.0.16000.28

* テーブル名に ";:" が含まれるデータベースをクリックするとクラッシュすることがあるという問題を修正しました。
* [AS Tabular Database Properties] (AS 表形式データベースのプロパティ) ウィンドウの [モデル] ページに変更を加えると、元の定義がスクリプト出力されるという問題を修正しました。 
[Microsoft Connect アイテム: 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* [最近使ったファイル] の一覧に一時ファイルが追加されるという問題を修正しました。  
[Microsoft Connect アイテム: 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* オブジェクト エクスプローラー ツリーのユーザー テーブル ノードで、[圧縮の管理] メニュー項目が無効になるという問題を解決しました。  
[Microsoft Connect アイテム: 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* オブジェクト エクスプローラー、登録済みサーバー エクスプローラー、およびテンプレート エクスプローラーのフォントサイズ、およびエクスプ ローラーの詳細をユーザーが設定できないという問題を解決しました。 エクスプローラーのフォントには、環境フォントが使用されます。  
[Microsoft Connect アイテム: 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* 接続が失われると、SSMS は常に既定のデータベースに再接続するという問題を解決しました。  
[Microsoft Connect アイテム: 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* 実行プラン アイコンを含む、ポリシー管理およびクエリ エディター ウィンドウで、多くの高 DPI 問題を修正しました。

* 拡張イベントのフォントと色を構成するためのオプションが見つからないという問題を修正しました。

* アプリケーションを閉じるとき、またはエラー ダイアログ ボックスが表示されるときに発生する SSMS のクラッシュの問題を修正しました。


## <a name="ssms-1641-september-2016-release"></a>SSMS 16.4.1 (2016 年 9 月) リリース
一般公開 | ビルド番号: 13.0.15900.1

*  ストアド プロシージャの ALTER/変更を実行しようとすると失敗するという問題を修正しました。  
[Microsoft Connect アイテム #3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* PowerShell でデータの表示や書き込みを行うための新しいコマンドレット 'Read-SqlTableData'、'Read-SqlViewData'、'Write-SqlTableData'。  
[Trello Read-SqlTableData カード](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Microsoft Connect アイテム #2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* 新しい 'Add-SqlLogin' コマンドレット。PowerShell を使った新しいログイン管理シナリオを可能にします。  
[Microsoft Connect アイテム #2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  さまざまな国のクラウドに接続するユーザーのためのサポートと使いやすさが向上しています。
    
    
*  メモリ不足例外がスローされるという問題を修正しました。  
[Microsoft Connect アイテム #3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Microsoft Connect アイテム #3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  スキーマによるフィルター処理というフィルター オプションを選択できないという問題を修正しました。  
[Microsoft Connect アイテム #3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Microsoft Connect アイテム #3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  ストレッチ データベースのモニター ウィンドウにアクセスできないという問題を修正しました。
    
*  F1 ヘルプで常にオンライン コンテンツが開くという問題を修正しました。 オンラインとオフラインのどちらのヘルプを参照するかを、[ヘルプ] メニューの "ヘルプ設定の設定" で選べるようになりました。   
[Microsoft Connect アイテム #2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  1200 レベルの Analysis Services 表形式モデルをスクリプト化するときに、パスワードがスクリプト用に除去されない (サーバー バージョンでは除去されていても) という問題を解決しました (クライアント モデル オブジェクトはスクリプト化の前に同期されるようになりました)。
    
*  'SELECT TOP N ROWS' オプションを選択すると、TOP 演算子について非推奨の構文が生成されるという問題を修正しました。  
[Microsoft Connect アイテム #3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  SSMS のさまざまなレイアウトの問題を修正しました。たとえば、[ログインのプロパティ] ページや詳細設定クエリ実行オプションです。   
[Microsoft Connect アイテム #3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Microsoft Connect アイテム #3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Microsoft Connect アイテム #3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  ユーザーが新しいクエリ ウィンドウを開くたびにソリューションが自動的に作成されるという問題を修正しました。   
[Microsoft Connect アイテム #2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Microsoft Connect アイテム #2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Microsoft Connect アイテム #2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  オブジェクト エクスプローラーでシステム データベースの中のテンポラル テーブルを拡張できないという問題を修正しました。  
[Microsoft Connect アイテム #2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  SSMS が SELECT @@trancount というクエリをバッチ実行後に実行するという問題を修正しました。    
[Microsoft Connect アイテム #3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  Analysis Services でスクリプトをサーバーのプロパティ ページから作成すると接続ダイアログが非表示になるという問題を修正しました。
    
*  Ctrl + Q キーを押してもクイック起動ツール バーが選択されないという問題を修正しました。
    
*  データベースの MaxSize を [サーバーのプロパティ] ダイアログで変更するときにデータベースが 2 TB を超えていると中断されるという問題を修正しました。  
[Microsoft Connect アイテム #1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  データベースの復元ウィザードで、先頭にホワイトスペースのあるファイル名が受け付けられないという問題を修正しました。   
[Microsoft Connect アイテム #2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="ssms-163-august-2016-release"></a>SSMS 16.3 (2016 年 8 月) のリリース
一般公開 |バージョン番号: 13.0.15700.28

* SSMS の毎月のリリースは番号が付けられるようになりました。

* [新しい認証オプション **「Active Directory ユニバーサル認証」**](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/)。 これは、多要素、パスワード、および統合認証メカニズムをサポートする Azure Active Directory によって実行されるトークン ベースの認証メカニズムです。

* SQL Server Profiler テンプレートの機能に適した新しい拡張イベント テンプレート [(Microsoft Connect アイテム #2543925)](https://connect.microsoft.com/SQLServer/feedback/details/2543925/sql-server-extended-events-profiler-tool)。 同梱の [SQL Server Profiler テンプレート](https://msdn.microsoft.com/library/ms190176.aspx)の詳細を表示します。

* Azure SQL データベースの新しい [データベースの作成] と [データベースのプロパティ] ダイアログ ボックス。

* PowerShell を使用して SQL Server ログインの管理を実行するための新しい ’Get SqlLogin’ コマンドレットと 'Remove-SqlLogin’ コマンドレット。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2588952。](https://connect.microsoft.com/SQLServer/feedback/details/2588952/)

* 任意のプロバイダーとキー パスの列マスター キーの作成のサポートを追加する新しい PowerShell コマンドレット ’New-SqlColumnMasterKeySettings’。

* SSMS での Azure SQL データベースの作成を効率化する新しい [データベースの作成] ダイアログ ボックス。

* SSMS オブジェクト エクスプ ローラーの 'データベース' のノードでのフィルタリングのサポート。 データベースの一覧をフィルター処理するには、オブジェクト エクスプ ローラーで 'データベース' ノードに移動し、オブジェクト エクスプ ローラーのツールバーでフィルター アイコンをクリックします。

* [バックアップと復元] ウィザードでの Azure Resource Manager (ARM) タイプのストレージ アカウントのサポート。

* [高解像度表示の初期ベータ版のサポート](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/)。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #1129301](https://connect.microsoft.com/SQLServer/feedback/details/1129301/management-studio-is-unusable-on-a-4k-display)、 [Microsoft Connect アイテム #1858763](https://connect.microsoft.com/SQLServer/feedback/details/1858763/)、 [Microsoft Connect アイテム #1852671](https://connect.microsoft.com/SQLServer/feedback/details/1852671/)、 [Microsoft Connect アイテム #1487643](https://connect.microsoft.com/SQLServer/feedback/details/1487643/)、  [Microsoft Connect アイテム #1355641](https://connect.microsoft.com/SQLServer/feedback/details/1355641/)、 [Microsoft Connect アイテム #2161595](https://connect.microsoft.com/SQLServer/feedback/details/2161595/)、 [Microsoft Connect アイテム #1854041](https://connect.microsoft.com/SQLServer/feedback/details/1854041/)、 [Microsoft Connect アイテム #1055617](https://connect.microsoft.com/SQLServer/feedback/details/1055617/)、 [Microsoft Connect アイテム #2448774](https://connect.microsoft.com/SQLServer/feedback/details/2448774/)、 [Microsoft Connect アイテム #1521405](https://connect.microsoft.com/SQLServer/feedback/details/1521405/)、 [Microsoft Connect アイテム #2117853](https://connect.microsoft.com/SQLServer/feedback/details/2117853/)、 [Microsoft Connect アイテム #2014256](https://connect.microsoft.com/SQLServer/feedback/details/2014256/)、 [Microsoft Connect アイテム #2162218](https://connect.microsoft.com/SQLServer/feedback/details/2162218/)、 [Microsoft Connect アイテム #2344551](https://connect.microsoft.com/SQLServer/feedback/details/2344551/)、 [Microsoft Connect アイテム #1664436](https://connect.microsoft.com/SQLServer/feedback/details/1664436/)、 [Microsoft Connect アイテム #2554043](https://connect.microsoft.com/SQLServer/feedback/details/2554043/)、 [Microsoft Connect アイテム #2983216](https://connect.microsoft.com/SQLServer/feedback/details/2983216/)、 [Microsoft Connect アイテム #2021706](https://connect.microsoft.com/SQLServer/feedback/details/2021706/)

* SQL Server クエリ ストアからのワークロードの自動読み取りをサポートするためのデータベース エンジン チューニング アドバイザー (DTA) を機能強化。

* クラスター化列ストア インデックス、非クラスター化列ストア インデックス、および行ストア インデックスに関するインデックスの推奨事項を表示するよう、データベース エンジン チューニング アドバイザー (DTA) を機能強化。

* SQL Server Analysis Services PowerShell コマンドレットを使用したデータベース コンソール (DBCC) コマンドの送信のサポート。

* SSMS で、復号化された AlwaysEncrypted ラージ オブジェクト (LOB) 列のクリア テキストを表示するようバグを修正。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2413024](https://connect.microsoft.com/SQLServer/feedback/details/2413024/cannot-view-cleartext-of-alwaysencrypted-lob-columns-in-ssms)

* Windows の視覚スタイルが有効でない場合のクラッシュを解決するよう [Always Encrypted] ダイアログボックスのバグを修正。

* SQL Server インスタンスへの接続を妨げる 'メソッドが見つかりませんでした' エラーのバグを修正。

* datetimeoffset を含むパーティション関数を作成するときの SSMS クラッシュのバグを修正。

* Distributed Replay 管理ツール (DReplay.exe) を起動するための Microsoft .NET 3.5 の削除要件を追加するようバグを修正。

* サーバーの完全修飾名をサポートするよう [Analysis Services 配置] ウィザードのバグを修正。

* 2016 互換性モデルの Analysis Services 表形式モデルでパーティションを表示するよう SSMS のバグを修正。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2845053](https://connect.microsoft.com/SQLServer/feedback/details/2845053/ssms-cannot-display-partitions-in-tabular-models-in-2016-compatibility-level) 

* Analysis Services 表形式モデルおよび SQL Server 共有管理オブジェクト (SMO) におけるパフォーマンスの改善およびバグの修正。 


---
## <a name="ssms-july-2016-hotfix-update-release"></a>SSMS 2016 年 7 月修正プログラムのリリース 
一般公開 |バージョン番号: 13.0.15600.2

* **不足している右クリック メニュー項目を有効にするよう SSMS のバグを修正**。  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2883440](https://connect.microsoft.com/SQLServer/feedback/details/2883440/lost-table-design-and-edit-top-n-rows-in-tables-context-menu)  
[Microsoft Connect アイテム #2909644](https://connect.microsoft.com/SQLServer/feedback/details/2909644/ssms-2016-is-missing-edit-options-against-sql-express-2014)  
[Microsoft Connect アイテム #2924345](https://connect.microsoft.com/SQLServer/feedback/details/2924345/some-ssms-object-explorer-right-click-menu-options-missing-in-july-update)

---
## <a name="ssms-july-2016-release"></a>SSMS 2016 年 7 月のリリース 
一般公開 |バージョン番号: 13.0.15500.91

* *7 月 5 日編集:* **Analysis Services プロセス ダイアログと Analysis Services の配置ウィザードの、表形式データベース向けの SQL Server 2016 (互換性レベル 1200) のサポートを強化。**

* *7 月 5 日編集:* **'XACT_ABORT' を設定する SSMS の [クエリ実行オプション] ダイアログ ボックスの新しいオプション。このオプションは、このSSMSリリースでは既定で有効になっています。実行時エラーが発生した場合に、SQL Server にトランザクション全体をロールバックし、バッチを中止する指示をします。**

* **SSMS での Azure SQL Data Warehouse のサポート。**

* **SQL Server PowerShell モジュールの大幅な更新。これには、新しい [SQL PowerShell モジュールと、Always Encrypted の新しいコマンドレット、SQL エージェント、SQL エラー ログ](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update)**が含まれます。

* **Always Encrypted ウィザードでの PowerShell スクリプトの生成のサポート**。

* **Azure SQL データベースへの接続時間を大幅に短縮。**

* **新しい 'Backup to URL' ダイアログによって、SQL Server 2016 データベースのバックアップ向けの Azure Storage の資格情報の作成をサポート。これにより、データベースのバックアップを Azure Storage アカウントにより効率的に格納できます。**
 
* **新しい復元ダイアログによって、Microsoft Azure Storage サービスからの SQL Server 2016 データベース バックアップの復元を効率化。**
 
* **ユーザーが SELECT 権限を持っていない場合に、SSMS クエリ デザイナーにテーブルを追加できるようバグを修正。**

* **'TRY_CAST()' と 'TRY_CONVERT()' 関数の IntelliSense サポートを追加するためのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2453461](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast)。

* **'SQLAS' Analysis Services 拡張機能の読み込みを有効にするための PowerShell モジュールのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2544902](https://connect.microsoft.com/SQLServer/feedback/details/2544902/ssms-march-2016-refresh-sqlps-failed-to-load-the-sqlas-extension)。

* **ドラッグ アンド ドロップで Sql ファイルを開くことができるよう、SSMS のエディター ウィンドウのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2690658](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios)。

* **終了時のプロファイラーのクラッシュを修正するようプロファイラーのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2616550](https://connect.microsoft.com/SQLServer/feedback/details/2616550/sql-server-2016-rc2-profiler-version-13-0-1300-275-wont-close-after-trace-is-started-even-after-trace-is-stopped)。  
[Microsoft Connect アイテム #2319968](https://connect.microsoft.com/SQLServer/Feedback/Details/2319968)。

* **SSMS テーブル デザイナーでの結合のリンクを編集しようとする際のクラッシュを防ぐよう、SSMS のバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2721052](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms)。

* **Db_owner ロールのメンバーのデータベース スクリプトの生成を有効にするよう SSMS のバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2869241](https://connect.microsoft.com/SQLServer/feedback/details/2869241/error-with-script-database-as-create-to-in-ssms-2008r2-and-ssms-2016-june)。

* **サーバーがオフラインになった場合、[クエリ] タブを閉じるときの遅延を回避するよう SSMS エディターのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2656058](https://connect.microsoft.com/SQLServer/feedback/details/2656058/ssms-2014-2016-query-tab-takes-significantly-longer-to-close-if-the-instance-it-was-connected-to-is-now-offline)。

* **SQL Server Express データベースのバックアップ オプションを有効にするようバグを修正。**  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2801910](https://connect.microsoft.com/SQLServer/feedback/details/2801910/ssms-2016-backup-option-not-appearing-in-tasks)。  
[Microsoft Connect アイテム #2874434](https://connect.microsoft.com/SQLServer/feedback/details/2874434/backup-missing-from-tasks-context-menu-in-ssms-2016-when-you-are-connected-to-an-express-instance)。

* **多次元の Analysis Services モデルのデータ フィード プロバイダーが正しく示されるよう、Analysis Services のバグを修正。**

----
## <a name="ssms-june-2016-generally-available-release"></a>SSMS 2016 年 6 月の一般公開リリース
一般公開 |バージョン番号: 13.0.15000.23

* **SSMS を 2016 年 6 月リリースから一般公開。**

* **現在のドキュメントへの統合が強化され、正規表現を使用した検索が可能な SSMS の新しいクイック検索ダイアログ。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/>

* **スクリプトを使用した無人インストールのインストール進行状況とプロセス終了コードを追跡できるよう、SSMS インストーラーを機能強化。**

* **ヘルプ ドキュメントおよび記事を正しく表示できるよう、SSMS の状況依存の F1 ヘルプのバグを修正。**

* **スクロール時に SSMS のクラッシュの原因となるクエリ データ ストア '低下したクエリ' ビューのバグを修正。** 

* **Excel 2016 から SQL Server Analysis Services への接続を許可するよう、Excel Analysis Services OLEDB コネクタのバグを修正。**

* **マルチ モニター システムで、SSMS のメイン ウィンドウと同じのモニターに [接続] ダイアログ ボックスを表示するよう、SSMS の [接続] ダイアログ ボックスのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/>
<https://connect.microsoft.com/SQLServer/feedback/details/755689/sql-server-management-studio-connect-to-server-popup-dialog/>  
<https://connect.microsoft.com/SQLServer/feedback/details/389165/sql-server-management-studio-gets-confused-dealing-with-multiple-displays/>

* **Always Encrypted エクスペリエンスのバグを修正。Always Encrypted メニュー オプションが Stretch Database に対して正しく有効にならないバグを修正しました。また、SafeNet (Luna SA) HSM プロバイダーを正しく使用しない Always Encrypted ウィザードのバグも修正しました。**

---
## <a name="ssms-april-2016-preview"></a>SSMS 2016 年 4 月プレビュー 
バージョン番号: 13.0.14000.36
  
* **人間が判読できるエラー メッセージを追加するための SSMS インストーラーの機能強化。**  
  
* **述語のサポートを追加するための Stretch Database ウィザードの機能強化**。  
  
* **キーの暗号化 API を追加するための AlwaysEncrypted Powershell コマンドレットの機能強化**。  
  
* **[ツール オプション] ダイアログ ボックスで IntelliSense を無効にしている場合、SSMS ツールバーで IntelliSense をオフにするようバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2555163/sql-2016-rc2-turning-off-intellisense-from-options-does-not-turn-it-off-on-toolbar/>  
    
* **時間のかかるクエリ プランで使用される間隔を減らすための、プラン表示の比較ユーザーインターフェイスの機能強化およびバグの修正**。  
  
* **SSMS を終了するとクラッシュの原因となった問題を修正するよう、SSMS のバグを修正**。   
  
* **暗号化中にユーザーのアクセス許可を保持し、ウィザードの完了後にデータベースによる操作のデタッチを許可するよう、Always Encrypted ウィザードのバグを修正**。  
  
* **サポートされていない暗号化アルゴリズム (CNG) プロバイダーを使用してキーを生成しようとしたときにフィールドバックを送信するための、Always Encrypted の [新しい列マスター キー] ダイアログ ボックスのバグを修正。**  
  
---  
## <a name="ssms-march-2016-preview-refresh"></a>SSMS 2016 年 3 月プレビューの更新
バージョン番号: 13.0.13000.55
  
* **SSMS では、Visual Studio 2015 の分離シェルを使用するようになりました。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2390544/update-ssms-to-use-visual-studio-2015-dependencies/>  
  
* **メニュー項目やオプションをすばやく見つけるのをサポートする新しいクイック起動ツールバー。(VS 2015 分離シェル)**  
  
* **SSMS ライト テーマのサポートを追加するための SSMS テーマ オプションの機能強化。(VS 2015 分離シェル)**  
  
* **[既定値にリセット] ボタンが押された場合にクエリのショートカットが正しくリセットされるよう、SSMS メニュー オプションを修正。**  
  
* **簡単に読み取り可能なテンプレートの名前を表示するよう、SSMS の新しいプロジェクト テンプレートのバグを修正。**  
  
* **SSMS で SQL エージェント ジョブ履歴を表示する際のエラーを解決。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2458860/error-viewing-job-history-microsoft-datawarehouse-sqm/>  
    
* **SSMS のオフライン インストールができるようバグを修正。これにより、インターネット接続がなくてもインストールできます。(VS 2015 分離シェル)**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2497178/cannot-install-ssms-when-server-has-no-internet-access/>  
    
* **SQL Server PowerShell (SQLPS) モジュールをインポートしたときにユーザーの現在のディレクトリが保持されるようバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2434605/loading-sqlps-module-changes-current-directory-to-ps-sqlserver/>  
    
* **承認済みの PowerShell 動詞を使用するよう SQL Server PowerShell (SQLPS) モジュールのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2432891/sqlps-module-uses-unapproved-powershell-verbs/>  
    
* **モジュールを高速に読み込むよう、SQL Server PowerShell (SQLPS) モジュールのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2429153/sqlps-module-is-slow-to-load/>  
    
* **ジョブ ステップの変更を許可するよう、SQL エージェント ジョブ ステップのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2453996/issues-with-agent-in-ssms-2016-rc0-13-0-12000-65/>  
    
* **アルファベット順にテーブルを一覧表示するよう、SSMS オブジェクト エクスプ ローラーのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2424718/sql-server-2016-ssms-table-list-confusing/>  
    
* **SQL Server の接続が変更されたときにデータベース名の正確な一覧が表示されるよう、[使用できるデータベース] ドロップダウン リストのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2513420/available-databases-drop-down-box-does-not-update-when-connection-changes-in-ssms/>  
    
* **'CTRL + U' のキーボード操作が行われたときに [使用できるデータベース] ドロップダウン リストにフォーカスを移動するよう、SSMS のキーボード ショートカットのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2534820/ssms-ctrl-u-doesnt-work/>  
  
---  
## <a name="ssms-march-2016-preview"></a>SSMS 2016 年 3 月プレビュー 
バージョン番号: 13.0.12500.29 
  
* **キーボードのキーを使用したナビゲーションを許可するための SSMS Web インストーラーの機能強化。**  
  
* **暗号化の別名データ型をサポートするための AlwaysEncrypted ウィザードの機能強化。**  
  
* **正しい数の最大の自動フェールオーバー ターゲットを表示するよう、AlwaysOn '新しい可用性グループ' ウィザードのバグを修正。**  
*リンクされている、顧客のバグ要求:* <https://connect.microsoft.com/SQLServer/feedback/details/2333670/ssms-is-showing-the-wrong-number-of-maximum-automatic-failover-targets/>  
    
* **インストールに影響するエラーを修正するために SSMS Web インストーラーのバグを修正。**  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2181548/sql-server-2016-ctp-3-2-management-studio-setup/>  
    
* **SQL Server 2012 以下のメンテナンスを保存できるよう、SSMS プレビュー リリースのバグを修正。**  
      
* **ストライプ バックアップに対して複数のカスタムバックアップ名を許可して、ストレージの資格情報を選択した後に新しい名前を入力した場合に適切なバックアップ ファイルの名前を表示するよう、バックアップ ウィザードのバグを修正。**  
  
---  
## <a name="ssms-february-2016-preview"></a>SSMS 2016 年 2 月プレビュー 
バージョン番号: 13.0.12000.65
  
* **SSMS でハイ コントラスト設定が有効になっているときに、テキストのオプションを表示するための利用状況モニターの機能強化。**  
  
* **列の照合順序が暗号化プロセス中に変更された場合に警告を表示するための Always Encrypted ウィザード ダイアログ ボックスの機能強化。**  
  
* **列暗号化キー、列暗号化キーの値、および列のマスター キーで条件を作成するためのサポートを追加するポリシー管理の機能強化。**  
  
* **Always Encrypted マスター キーのクリーンアップのダイアログの使いやすさおよび Always Encrypted エラー メッセージを改善するようバグを修正。**  
  
* **キーが 1 つしか存在しない場合に Always Encrypted 列マスター キーの交換を無効にするようバグを修正。**  
  
* **SSMS 1 月リリース、または SQL Server RC0 メディアにバンドルされている SSMS リリースを使用して Always Encrypted を起動した場合に発生する '型の初期化子' エラーのバグを修正。**  
  
---  
## <a name="ssms-january-2016-preview"></a>SSMS 2016 年 1 月プレビュー 
バージョン番号: 13.0.11000.78 
  
* **拡張イベント (XEvent) セッションを削除できるようにするための SSMS でのバグ修正。**  
  
* **SQL Server 2014 可用性グループのプロパティ ダイアログを開くためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/1609719/>  
     
* **Azure のレプリカを可用性グループに追加する機能を有効にするためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2029135/>  
     
* **SQL Server 2014 データベースのプロパティ ダイアログを開くためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2080209/>  
     
* **Azure SQL Database への接続時に各テーブルに表示される重複した列を削除するためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2103116/>  
---  
## <a name="ssms-december-2015-preview"></a>SSMS 2015 年 12 月プレビュー 
バージョン番号: 13.0.900.73
  
* **現在のクエリ実行プランとファイルに保存されたプランとの比較を可能にする Showplan 比較の機能強化。**  
  
* **SSMS でのインライン列ストア インデックスの IntelliSense サポート強化。**  
  
* **Azure V12 サーバーに接続しているときにテンプレートの選択を有効にする拡張イベント セッション ウィザードのバグ修正。**  
  
* **[セキュリティ] フォルダーの [監査の作成] と [新しいログイン] ダイアログのタブ位置が新しくなり、キーボードの操作性が向上。**  
  
* **グリッド形式で結果を表示するように SSMS を設定した場合に、"クエリ実行後に [結果] タブに切り替える" 機能を有効にするためのバグ修正。**   
 *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1390296/switch-to-results-tab-after-query-execution-grid-mode-in-ssms-2016>  
  
* **SSMS をグリッド形式で結果を表示するように設定した場合に、切り詰められていない列ヘッダーを表示するためのバグ修正。**  
 *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/2004111/bugbash-column-headers-in-grid-mode-truncated-with-courier-new-8>  
      
* **バグ修正により、SSMS Web インストーラーの適切なインストールが可能。**  
 *リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2003865/ssms-october-preview-incoherent-error-message>  
<https://connect.microsoft.com/SQLServer/feedback/details/2079557/unable-to-instal-sql-server-update-13-0-800-111-over-13-0-700-242-error-code-2711>  
  
---  
## <a name="ssms-november-2015-preview"></a>SSMS 2015 年 11 月プレビュー
バージョン番号: 13.0.800.111
  
* **SSMS の高解像度用ディスプレイ ビットマップ スケーリングをサポート。**  
  
* **AlwaysEncrypted ダイアログとウィザードのユーザー インターフェイスを改善し、データベース暗号化キーの作成プロセスを簡略化。**  
  
* **[Activity] モニターの [プロセス] 一覧に追加された新しい右クリック コンテキスト メニュー オプションで Live Query 統計情報を表示。**  
  
* **バグ修正により、クライアント コンピューターで SSMS プレビュー リリースの適切なアンインストールが可能。**  
  *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1868474/ssms-2016-preview-can-be-installed-but-not-uninstalled>  
  
* **ファイルがなくても SQL ジョブ エージェントのジョブ ステップの編集を許可するためのバグ修正**。  
  *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1769778/management-studio-2016-sql-job-agent>  
    <https://connect.microsoft.com/SQLServer/feedback/details/1502100/ssms-preview-error>  
      
* **Azure の仮想マシンで実行しているデータベースの拡張イベント セッションの [ターゲット データの表示] メニュー オプションのバグ修正。**  
  *リンクされている、顧客のバグ要求*:  
  <https://connect.microsoft.com/SQLServer/feedback/details/1769778/management-studio-2016-sql-job-agent>  
***  

## <a name="ssms-october-2015-preview"></a>SSMS 2015 年 10 月プレビュー 
バージョン番号: 13.0.700.242  
* **新しく革新的で軽量な Web インストーラー。SSMS のダウンロードとインストールのプロセスを簡略化します。**  
  
* **新しい Always Encrypted 列暗号化ウィザード。クライアント側での選択した列の暗号化と復号化が可能です。**  
  
* **新しい列マスター キー (CMK) 回転ダイアログ。Always Encrypted データベース用で、データを保護するための暗号化キーの回転プロセスを簡略化します。**  
  
* **新しいストレッチ データベース モニター。Azure クラウドへのデータ移行の状態のトラブルシューティングと監視を行うことができます。**  
  
* **Stretch Database ウィザードの機能強化。既定では Microsoft Azure サブスクリプションに含まれない Microsoft Azure サーバーの選択をサポートしています。**  
  *リンクされている、顧客のバグ要求:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1687063/cannot-choose-from-multiple-microsoft-azure-subscriptions>  
* **SSMS でライブ実行プランを適切に表示できるようにするためのバグ修正。**  
  *リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1774446/viewing-live-execution-plan-from-activity-monitor-crashes-ssms>    
* **データベース スナップショットの SSMS スクリプトにおける無効なオプションを削除するためのバグ修正**  
  *リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1515168/ssms-scripting-of-database-snapshots-includes-invalid-options>  
* **[トップ リソースのコンシューマー クエリ] ウィンドウで詳細を表示するためのクエリ データ ストア UI のバグ修正。**  
  *リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1737185/sql-server-2016-overall-resource-consumption-query-store-pane-issue>  
***  

## <a name="ssms-september-2015-preview"></a>SSMS 2015 年 9 月プレビュー 
バージョン番号: 13.0.600.65  
* **Azure SQL Database への接続プロセスを効率化する、新しいファイアウォール ルール ダイアログ。**      
    
* **[新しいインデックス] ダイアログの更新。クラスター化列ストア インデックスが存在する場合でもクラスター化されていない行ストア インデックスを作成できます。この機能は、SQL 2016 以降で利用できます。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1552617/creation-of-nc-index-when-clustered-columnstore-index>  
      
* **Windows 7 で実行される SSMS プレビュー版リリースの SQL エージェント ジョブ ステップを表示と編集できるようにするためのバグ修正。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1548140/cannot-view-or-edit-any-sql-agent-job-step>    
  <https://connect.microsoft.com/SQLServer/feedback/details/1626895/unable-to-load-dll-dts>    
  <https://connect.microsoft.com/SQLServer/feedback/details/1576662/error-creating-new-job-step>     
      
* **SQL Server 2014 以降の SSMS におけるトリガー ノードを表示するためのバグ修正。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1617533/trigger-node-missing>   
      
* **ヘッダーからバージョン情報を除外するための、データベースとサーバーの標準レポート ユーザー インターフェイスにおけるバグ修正。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1387471/report-headings-wrongly-named>  
      
* **ライブ クエリ統計ノードで、完了していないにもかかわらず完了と表示されないようにするためのバグ修正。**      
  *リンクされている、顧客のバグ要求:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1589096/live-query-statistics-node-shows-as-completed>  
  
***      
## <a name="ssms-august-2015-preview"></a>SSMS 2015 年 8 月プレビュー 
バージョン番号: 13.0.500.53
  
* **オブジェクト エクスプローラーの更新。データベースが多数存在する場合の読み込み遅延を減らします。**  
  
* **Windows 10 コンピューターでの SSMS インストールの機能強化。**  
  
* **SQL Server 構成マネージャーと SSMS ユーザー レポートのユーザー インターフェイスのバグ修正と更新。**    
***  
  
## <a name="ssms-july-2015-preview"></a>SSMS 2015 年 7 月プレビュー
バージョン番号: 13.0.400.91
  
* **Azure SQL Database (V12) のデータベース ダイアグラム。**  
  
* **新しいテンポラル テーブル構文に関する IntelliSense サポートの強化。**  
  
* **DacFx library ライブラリの更新。行レベルのセキュリティと Azure Active directory 認証を含む最新の Azure SQL Database 機能をサポートします。**  
  
* **バグ修正 ([更新プログラムの確認] UI の更新、[互換性レベル] 一覧などにおける UI 修正)。**  
***  
  
## <a name="ssms-june-2015-preview"></a>SSMS 2015 年 6 月プレビュー 
バージョン番号: 13.0.300.44
  
* **SSMS の新しい軽量 Web インストーラー。**  
  
* **自動的な更新プログラムの確認。**  
  
* **SSMS で、Azure SQL Database (V12) のフル テキスト検索をサポートするようになりました。**  
  
* **お客様から要求が最も多い次の問題に対応しました。**  
  * オブジェクト エクスプローラーのテーブルとビューに関して [上位 200 行を編集] を利用できるようになりました。  
  * Azure SQL Database (V12) に関してテーブル デザイナーを使用できます。  
  * Azure SQL Database (V12) で、データベースとテーブルのプロパティのダイアログを使用できるようなりました。  
    
 * **T-SQL ファイルを保存するように求めるメッセージをスキップする新しいオプション。**  
   
 * **新しい Azure SQL Database サービス レベル (Basic、Standard、Premium) での Import/Export ウィザードのサポート。**  
   
 * **多くのバグ修正 (スクリプト作成シナリオ、SQL データベースの変更追跡の有効化など)。**   

