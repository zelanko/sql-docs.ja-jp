---
title: SQL Server Management Studio - Changelog (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 12/19/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c854d2e332d38443646de560a906826c419705b7
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2019
ms.locfileid: "54300549"
---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  > [!div class="nextstepaction"]
  > [SQL ドキュメントの目次に関するご意見を共有してください。](https://aka.ms/sqldocsurvey)

この記事では、SSMS の現在と以前のバージョンの更新、機能強化、およびバグの修正に関する詳細を提供します。 [SSMS の以前のバージョン](#previous-ssms-releases)をダウンロードします。



## <a name="ssms-180-preview-6download-sql-server-management-studio-ssmsmd"></a>[SSMS 18.0 (プレビュー 6)](download-sql-server-management-studio-ssms.md)

ビルド番号:15.0.18075.0<br>
リリース日:2018 年 12 月 18 日

プレビュー 6 は、SSMS 18.0 の最初のパブリック プレビューです。 最新の一般公開 (GA) バージョンの SSMS については、[SSMS 17.9.1 をダウンロードしてインストールしてください](#ssms-1791-latest-ga-release)。

### <a name="whats-new-in-preview-6"></a>プレビュー 6 の新機能

このセクションでは、SSMS 18.0 プレビュー 6 の新機能を一覧表示します。 SSMS 17.9.1 以降の完全な変更ログについては、「[SSMS 18.0 preview - cumulative changelog through preview 6](#ssms-180-preview---cumulative-changelog-through-preview-6)」(SSMS 18.0 プレビュー - プレビュー 6 までの累積的な変更ログ) を参照してください。

- **SSMS**
  - [ツール] メニューに [Azure への移行] が追加されました。[Data Migration Assistant](https://aka.ms/get-dma) と [Azure Database Migration Service](https://aka.ms/get-dms) を統合することで、すばやく簡単にアクセスして Azure により迅速に移行できるようにしました。
  - 以前のバージョン (プレビュー 6 より前) の SSMS 18.0 では、"利用可能なデータベース" キー ショートカットが **CTRL + ALT + J** キーにバインドされていました。 プレビュー 6 以降では、キー バインドが、SSMS 17.x と同様に、**CTRL + U** キーに復元されています。
  - "接続の変更" が使用されている場合に、ユーザーに開いているトランザクションをコミットするよう求めるロジックが追加されました。

- **SSIS**
  - SSMS で MI の SQL エージェントを使用するときに、SSIS エージェント ジョブ ステップでパラメーターと接続マネージャーを構成できます。


### <a name="bug-fixes"></a>バグの修正

- **SSMS エディター**
  - 新しい TRANSLATE 関数が、Intellisense によって認識されるようになりました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430 を参照してください。
  - 組み込み関数 FORMAT の Intellisense が改善されました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676 を参照してください。
  - LAG と LEAD が組み込み関数として認識されるようになりました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757 を参照してください。
  - "ALTER TABLE...ADD CONSTRAINT...WITH(ONLINE=ON)" の使用時に IntelliSense で警告が表示されていた問題が修正されました

- **オブジェクト スクリプト作成**
  - Azure SQL Database で GEOMETRY_AUTO_GRID/GEOGRAPHY_AUTO_GRID を使用して、空間インデックスのスクリプトを作成しようとするとエラーがスローされていた問題が修正されました。

- **SMO**
  - SMO を使用して作成されたアプリケーションで、複数のスレッドで同じサーバーのデータベースを列挙しようとした場合に、各スレッドで別の SqlConnection インスタンスを使用していてもエラーが発生していた問題が修正されました。

- **データ分類**
  - データ分類ウィンドウで分類を保存するときに、他のデータベースで別のデータ分類ウィンドウが開いている問題が修正されました。

- **Azure SQL Database**
  - Azure の [統計] メニューの下にある統計プロパティのサブメニュー オプションを有効にしました。これは、もうだいぶ前から完全にサポートされていたためです。

- **クエリ データ ストア**
  - "DocumentFrame (SQLEditors)" 例外がスローされる可能性がある問題が修正されました。
  - 組み込みのクエリ ストア レポートでカスタム時間間隔を設定しようとしたときに、ユーザーが開始/終了間隔で AM や PM を選択できなかった問題が修正されました。

- **データベース コピー ウィザード**
  - スクリプトの生成/転送/データベース コピー ウィザードでインメモリ テーブルを使用してテーブルを作成しようとすると、ansi_padding on が強制されません。
  - SQL Server 2017 および SQL Server 2019 のデータベース転送タスク/データベース コピー ウィザードは壊れています。
  - スクリプトの生成/転送/データベース コピー ウィザードでは、関連付けられている外部データ ソースが作成される前に、テーブルの作成がスクリプト化されます。

- **Profiler**
  - Profiler イベントに "Aggregate Table Rewrite Query" イベントが追加されました。

- **プラン表示**
  - 複数のスレッドが存在する場合、新しい mem grant 演算子プロパティが正しく表示されません。

### <a name="known-issues"></a>既知の問題

- .sql ファイルをダブルクリックすると SSMS が起動しますが、実際のスクリプトは開きません。
  - 回避策: .sql ファイルをドラッグし、SSMS エディターにドロップします。

## <a name="ssms-180-preview---cumulative-changelog-through-preview-6"></a>SSMS 18.0 プレビュー - プレビュー 6 までの累積的な変更ログ

*プレビュー 5* や*プレビュー 6* のラベルがない場合は、SSMS 18.0 の最初のパブリック プレビュー (SSMS 18.0 *プレビュー 4*) での変更を示しています。

### <a name="whats-new"></a>新機能

- **SSMS**
  - ダウンロード サイズの縮小
    - バンドルの現在のサイズは SSMS 17.x の半分未満です (400 MB 以下)。 このサイズは、IS コンポーネントが SSMS に再び追加されると最終的に少し大きくなりますが、従来ほど大きくなりません。
  - SSMS は新しい VS 2017 Isolated Shell に基づいています
    - つまり、最新のシェルです (VS 2107 15.6.4 を選択しました)。 新しいシェルで、SSMS と Visual Studio の両方で行われたアクセシビリティに関するすべての修正のロックが解除されます。
  - SSMS アクセシビリティの機能強化
    - すべてのツール (SSMS、DTA、Profiler) のアクセシビリティの問題を解決するためにさまざまな作業が行われました
  - SSMS はカスタム フォルダーにインストールできます
    - 現在のところ、これはコマンドラインの設定でのみ使用できます。 この追加の引数を SSMS-Setup-ENU.exe に渡します。
      - SSMSInstallRoot=C:\MySSMS18
      - 既定では、SSMS の新しいインストール先は次のとおりです。
      - %ProgramFiles(x86)%\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe
      - 注: これは、SSMS がマルチインスタンスであるという意味ではありません。
  - SSMS では、SQL エンジンとコンポーネントを共有しなくなりました
    - SQL エンジンとコンポーネントを共有しないようにさまざまな作業が行われました。このような共有によって、保守性の問題 (他のコンポーネントによってインストールされたファイルが上書きされる) が発生することがよくあります。
  - SSMS には NetFx 4.7.2 以降が必要です
    - 最小要件を NetFx4.6.1 から NetFx4.7.2 にアップグレードしました。これにより、新しいフレームワークで公開されている新しい機能を利用できるようになります。
  - SSMS は Windows 8 と Windows Server 2012 ではサポートされていません。Windows 10 / Windows Server 2016 にはバージョン 1607 (10.0.14393) 以降が必要になります
    - NetFx 4.7.2 への新しい依存関係があるため、SSMS 18.0 は、Windows 8 と Windows Server 2012 および以前のバージョンの Windows 10 と Windows Server 2016 にはインストールされません。 このような OS では、SSMS の設定はブロックされます。 注:"Windows 8.1" は引き続きサポートされます。
  - SSMS は PATH 環境変数に追加されません
    - SSMS.EXE (および一般的なツール) のパスは、パスに追加されなくなりました。 ユーザーは手動で追加するか、最新の Windows の場合は [スタート] メニューを使用することができます。
  - SQL Server SQL 2019 のサポート
    - これは、SQL Server 2019 を完全に認識する最初のリリースの SSMS です (compatLevel 150 など)
    - SQLSERVER2018 の "BATCH_STARTED_GROUP" と "BATCH_COMPLETED_GROUP" および SSMS のマネージド インスタンスがサポートされます
    - UDF のインライン化のための SMO サポート
    - GraphDB:Graph TC Sequence のプラン表示にフラグが追加されます
    - Always Encrypted: AEv2 / エンクレーブのサポートが追加されました
    - Always Encrypted: ユーザーがエンクレーブのサポートを有効にする/構成する [オプション] ボタンをクリックすると、新しいタブの [Always Encrypted] が表示されます。
  - SSMS 拡張機能を開発するためにパッケージ ID が不要になりました
    - これまで、SSMS では既知のパッケージのみが選択されて読み込まれていたので、開発者は自分のパッケージを登録する必要がありました。 この点は変更されました。
  - 高 DPI のサポートは既定で有効になります
  - Azure SQL Database サポートの改善
  - SLO/Edition/MaxSize データベース プロパティにカスタム名を使用できるようになり、今後のエディションの SQL Azure データベースのサポートが簡単になりました
  - 最近追加された仮想コア SKU (General Purpose および Business Critical) のサポートの追加:Gen4_24 およびすべての Gen5。
  - SSMS の Filegroups に関する AUTOGROW_ALL_FILES 構成オプションの公開
  - SSMS GUI から、危険な 'lightweight pooling' および 'priority boost' オプションを削除しました (詳細については、 https://blogs.msdn.microsoft.  com/arvindsh/2010/01/26/priority-boost-details-and-why-its-not-recommended/ を参照)。
  - SQL エディターで行の複製に CTRL + D ショートカット キーを使用できるようになりました。詳細については、こちら (https://feedback.azure.com/forums/908035-sql-server/suggestions/32896594) を参照してください
  - ファイルを作成するための新しいメニューとキー バインド:CTRL + ALT + N。 CTRL + N でも引き続き新しいクエリを作成できます。 注: "SSMS 18.0 プレビュー 1" から移行する場合は、**[ツール] | [設定のインポートとエクスポート] | [すべての設定をリセット]** でユーザー設定をリセットする必要があります。
  - [新しいファイアウォール規則] ダイアログで、自動的に生成される規則名ではなく、ユーザーが規則名を指定できるようになりました。詳細については、こちら (https://feedback.azure.com/forums/908035-sql-server/suggestions/32902039)= を参照してください
  - データの分類: 推奨事項が更新されました
  - 特に v140 T-SQL に合わせてエディターの IntelliSense が改善されました
  - SSMS UI の照合順序ダイアログに UTF-8 のサポートが追加されました。
  - 接続ダイアログの MRU パスワードの場合に [Windows Credential Manager] に切り替わりました。 これで、パスワードの持続性が信頼できない場合があった長時間保留の問題が解決されます。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32896486 を参照してください。
  - 目的のモニター上にダイアログとウィンドウのポップアップがより多く表示されるように、マルチモニター システムのサポートが改善されました。
  - [サーバーのプロパティ] ダイアログの新しい [データベースの設定] ページで、'バックアップ チェックサムの既定値' サーバー構成を公開しました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/34634974 を参照してください
  - (プレビュー 5 の新機能) [SQL Server エラー ログの構成] の下に "エラー ログ ファイルの最大サイズ" を公開しました。 詳細については、 https://feedback.azure.com/forums/908035/suggestions/33624115 を参照してください 
  - (プレビュー 6 の新機能) [ツール] メニューに [Azure への移行] が追加されました。[Data Migration Assistant](https://aka.ms/get-dma) と [Azure Database Migration Service](https://aka.ms/get-dms) を統合することで、すばやく簡単にアクセスして Azure により迅速に移行できるようにしました。
  - (プレビュー 6 の新機能) 以前のバージョン (プレビュー 6 より前) の SSMS 18.0 では、"利用可能なデータベース" キー ショートカットが **CTRL + ALT + J** キーにバインドされていました。 プレビュー 6 以降では、キー バインドが、SSMS 17.x と同様に、**CTRL + U** キーに復元されています。
  - (プレビュー 6 の新機能) "接続の変更" が使用されている場合に、ユーザーに開いているトランザクションをコミットするよう求めるロジックが追加されました。

- **SMO**
  - 再開可能なインデックス作成の SMO サポートを拡張します
  - アプリケーション作成者が SMO のパフォーマンスの問題を早期に検出できるように、SMO オブジェクト ("PropertyMissing") に対する新しいイベントを追加しました。  
  - "バックアップ チェックサムの既定" サーバー構成にマップされる、Configuration オブジェクトに対する新しい DefaultBackupChecksum プロパティを公開しました
  - (プレビュー 5 の新機能) 使用中の SQL のバージョンのサービス レベル (CU12、RTM など) にマップする、新しい ProductUpdateLevel プロパティをサーバー オブジェクト上に公開しました
  - (プレビュー 5 の新機能) "lastgoodcheckdbtime" データベース プロパティにマップする、新しい LastGoodCheckDbTime プロパティをデータベース オブジェクト上に公開しました。 これらのプロパティが使用できない場合、既定値の 1/1/1900 12:00:00 AM が返されます。
  - (プレビュー 5 の新機能) RegSrvr.xml ファイル (登録済みサーバーの構成ファイル) の場所を "%AppData%\Microsoft\SQL Server Management Studio" に移動しました (バージョン管理されないため、SSMS のバージョン間で共有できます)

- **Azure Data Studio との統合**
  - Azure Data Studio を起動/ダウンロードするためのメニュー項目が追加されました
  - (プレビュー 5 の新機能) オブジェクト エクスプローラーに [Azure Data Studio の起動] メニュー項目が追加されました

- **プラン表示**
  - 使用できる場合、ShowPlan 演算子ノードに実際の経過時間、実際の行と推定の行が追加されました。 これで、実際のプランが、ライブ クエリの統計プランと一貫した外観になります。
  - クエリが 4,000 文字を超える場合に、SQL エンジンによって ShowPlan が切り捨てられる可能性があることをユーザーに示すために、ShowPlan の [クエリの編集] ボタンをクリックしたときのツールヒントが変更され、コメントが追加されました。
  - "Materializer Operator (External Select)" を表示するロジックが追加されました
  - "行ストアに対するバッチモード スキャン" 機能を使用しているクエリを簡単に識別できるように、新しい showplan 属性 BatchModeOnRowStoreUsed を追加します。 クエリが行ストアでバッチモード スキャンを実行するたびに、新しい属性 (BatchModeOnRowStoreUsed="true") が StmtSimple 要素に追加されます。

- **データベース互換性レベルのアップグレード**
  - (プレビュー 5 の新機能) [タスク] <Database name> [データベースのアップグレード] の下に新しいオプションが追加されました。 これにより、ユーザーに次のプロセスをガイドする、新しいクエリ調整アシスタント (QTA) が開始されます。
    - データベースの互換性レベルをアップグレードする前にパフォーマンスのベースラインを収集する。 
    - 目的のデータベース互換性レベルにアップグレードする
    - 同じワークロードを介してパフォーマンス データの 2 番目の受け渡しを収集する。
    - ワークロードの低下を検出し、ワークロードのパフォーマンスを改善するためのテスト済みのレコメンデーションを提供する。

  これは、 https://docs.microsoft.com/sql/relational-databases/performance/query-store-usage-scenarios#CEUpgrade に記載されているデータベースのアップグレード プロセスに似ていますが、最後の手順 (レコメンデーションを生成するために QTA が以前の正常起動時の状態に依存しない) が異なります。

- **クエリ ストア**
  - (プレビュー 5 の新機能) グラフの Y 軸に表示される数字に桁区切り記号を追加することで、一部のレポート (全体的なリソースの消費) の使いやすさを改善しました。
  - (プレビュー 5 の新機能) 新しいクエリ待機統計レポートが追加されました。

- **データ マスク**
  - (プレビュー 5 の新機能。2018 年 11 月 4 日に追加) 静的データ マスクが追加されました。 静的データ マスクは、ユーザーが自身の SQL データベースをコピーして、コピー上の機密データをマスクできるようにするデータ保護ツールです。 この機能は、開発/テスト チームや分析チームなどの実稼働データベースを使用していないユーザーと実稼働データベースを共有するのに役立ちます。 詳細については、「[Static Data Masking for Azure SQL Database and SQL Server](https://azure.microsoft.com/blog/static-data-masking-preview/)」 (Azure SQL Database および SQL Server 用の静的データ マスク) を参照してください。

- **Always On**
  - SSMS の Always on ダッシュボードで RTO (推定復旧時間) と RPO (推定データ損失) を再ハッシュします。 ドキュメントは、 https://docs.microsoft.com/sql/database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups で更新されています

- **監査ファイル**
  - 認証方法をストレージ アカウント キー ベースから Azure AD ベースの認証に変更しました

- **SSIS**
  - (プレビュー 5 の新機能) 顧客が Azure Government クラウド内にある Azure-SSIS IR で SSIS パッケージをスケジュールできるようにするためのサポートが追加されました
  - (プレビュー 6 の新機能) SSMS で MI の SQL エージェントを使用するときに、SSIS エージェント ジョブ ステップでパラメーターと接続マネージャーを構成できます。

- **データ分類**
  - データ分類タスク メニューを再構成しました。データベース タスク メニューにサブメニューが追加され、最初に分類データ ウィンドウを開かなくても、メニューからレポートを開くためのオプションが追加されました。

- **脆弱性評価**
  - (プレビュー 5 の新機能) SQL DW で脆弱性評価タスク メニューが有効になりました。

- **Always Encrypted**
  - [サーバーに接続] ダイアログの新しい [Always Encrypted] タブにある [Always Encrypted を有効にする] チェックボックスで、データベース接続での Always Encrypted の有効化/無効化を簡単に切り替えられるようになりました。 

- [**セキュリティで保護されたエンクレーブが設定された Always Encrypted**](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves)
  - SQL Server 2019 プレビューでは、セキュリティで保護されたエンクレーブが設定された Always Encrypted をサポートするためにいくつかの機能強化が加えられました
    - [サーバーに接続] ダイアログ (新しい [Always Encrypted] タブ) にエンクレーブの構成証明の URL を指定するテキスト フィールド。
    - 新しい列マスター キーでエンクレーブ計算を許可するかどうかを制御する、[新しい列マスター キー] ダイアログの新しいチェックボックス。
    - 他の Always Encrypted キー管理ダイアログに、エンクレーブ計算を許可する列マスター キーの情報が表示されるようになりました。


### <a name="bug-fixes"></a>バグの修正

- **クラッシュ / ハング**
  - GDI オブジェクトに関連する一般的な SSMS クラッシュの原因を修正しました
  - [Script as Create/Update/Drop]\(作成/更新/ドロップとしてスクリプト化\) を選択したときの停止とパフォーマンス低下の一般的な原因を修正しました (SMO オブジェクトの不要なフェッチを削除しました)
  - ADAL トレースが有効なときに MFA を使用して Azure SQL DB に接続するとハングする問題を修正しました
  - アクティビティ モニターから呼び出されたときにライブ クエリの統計情報のハングを修正しました ([セキュリティ情報を保持する] を設定せずに SQL Server 認証を使用するときにマニフェストに含まれる問題)。
  - オブジェクト エクスプローラーで [レポート] を選択したときのハングを修正しました。この問題で、長い接続の待機時またはリソースの一時的にアクセス不能に関するマニフェストが含まれる可能性があります。
  - (プレビュー 5 の新機能) 中央管理サーバーと SQL Azure サーバーを使用しようとしたときの、SSSM のクラッシュが修正されました。 詳細については、 https://feedback.azure.com/forums/908035/suggestions/33374884 を参照してください。 
  - (プレビュー 5 の新機能) IsFullTextEnabled プロパティを取得する方法を最適化することによって、オブジェクト エクスプローラーでのハングが修正されました
  - (プレビュー 5 の新機能) データベース プロパティを取得する不要なクエリの作成を回避することで、"データベース コピー ウィザード" でのハングが修正されました

- **接続ダイアログ**
  - Del キーを押して、以前のユーザー名リストからユーザー名を削除できるようになりました。詳細については、こちら (https://feedback.azure.com/forums/908035/suggestions/32897632) を参照してください

- **XEvent**
  - 読み込みできる文字列としてアクション ID フィールドとクラスの型フィールドを示す 2 つの列 "action_name" と "class_type_desc" が追加されました。
  - 1,000,000 イベントのイベント XEvent Viewer 上限を削除しました。

- **外部テーブル**
  - テンプレート、SMO、IntelliSense、プロパティ グリッドに Rejected_Row_Location のサポートが追加されました

- **SSMS のオプション**
  - **[ツール] | [オプション] | [SQL Server オブジェクト エクスプローラー]** | [コマンド] ページのサイズが正しく変更されない問題を修正しました。
  - SSMS では既定で、XMLA エディターでの DTD の自動ダウンロードが無効化されるようになります。(xml 言語サービスを使用する) XMLA スクリプト エディターでは既定で、悪意がある可能性のある xmla ファイルの DTD が自動的にダウンロードされないようになります。  これは、[ツール] -> [オプション] -> [環境] -> [テキスト エディター] -> [XML] -> [その他] で [DTD とスキーマを自動的にダウンロードする] 設定をオフにすることで制御されます。  
  - (プレビュー 5 の新機能) 以前のバージョンの SSMS にあった CTRL + D のショートカットを復元しました。 詳細については、 https://feedback.azure.com/forums/908035/suggestions/35544754 を参照してください

- **SSMS エディター**
  - "SQL システム テーブル" の問題を修正しました。この問題で、既定の色を復元すると、既定の緑色ではなく、ライム グリーン色に変わり、白い背景では非常に読みにくくなります。詳細については、こちら (https://feedback.azure.com/forums/908035-sql-server/suggestions/32896906) を参照してください
  - AAD 認証を使用して Azure SQLDW に接続したときに IntelliSense が動作しない問題を修正しました。
  - ユーザーがマスター アクセス権を持たない場合の Azure の IntelliSense が修正されました
  - ターゲット データベースの照合順序で大文字と小文字が区別されているときに破損した "一時テーブル" が作成されるコード スニペットを修正しました。
  - (プレビュー 6 の新機能) 新しい TRANSLATE 関数が、Intellisense によって認識されるようになりました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430 を参照してください
  - (プレビュー 6 の新機能) 組み込み関数 FORMAT の Intellisense が改善されました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676 を参照してください
  - (プレビュー 6 の新機能) LAG と LEAD が組み込み関数として認識されるようになりました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757 を参照してください
  - (プレビュー 6 の新機能) "ALTER TABLE...ADD CONSTRAINT...WITH(ONLINE=ON)" の使用時に IntelliSense で警告が表示されていた問題が修正されました

- **[オブジェクト エクスプローラー]**
  - OE (誤って構成された DataCollector) の [管理] ノードを展開しようとすると、SSMS から "オブジェクトを DBNull から他のタイプにキャストすることはできません" のような例外がスローされる問題を修正しました。
  - ノードの名前を変更するときに、Del キーが機能しない問題を修正しました (詳細については、 https://feedback.azure.com/forums/908035/suggestions/32910247 と他の重複を参照)
  - [上位 N の編集] を呼び出す前に OE で引用符がエスケープ処理されず、混乱を引き起こしている問題を修正しました
  - [データ層アプリケーションのインポート] ウィザードが Azure Storage ツリーから起動できない問題を修正しました。
  - SSL チェックボックスの状態が保持されない [データベース メール構成] の問題を修正しました。詳細については、こちら (https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541) を参照してください
  - SSMS で is_auto_update_stats_async_on を使用してデータベースを復元しようとすると、既存の接続を閉じるオプションが淡色表示される問題を修正しました
  - OE のノードを右クリックしたときの問題を修正しました (たとえば、"Tables" では、[フィルター] > [フィルターの設定] に移動して、テーブルのフィルター処理などの操作を実行したい場合、フィルターの設定フォームが、SSMS が現在アクティブではない他の画面に表示される可能性があります)。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106 を参照してください。
  - オブジェクトの名前を変更しようとすると、OE で Del キーが機能しないという、長い間未解決の問題が修正されました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510 を参照してください
  - 既存のデータベース ファイルのプロパティを表示すると、新しいデータベースの作成時に表示される [初期サイズ (MB)] ではなく [サイズ (MB)] 列にサイズが表示されます。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024 を参照してください
  - 現在のバージョンの SSMS ではこの種のテーブルをサポートしていないため、[グラフ テーブル] の [デザイン] コンテキスト メニュー項目を無効にしました。
  - (プレビュー 5 の新機能。インサイクル) [新しいジョブ スケジュール] ダイアログが高 DPI モニターで正しくレンダリングされない問題を修正しました。 詳細については、 https://feedback.azure.com/admin/v3/suggestions/35541262 を参照してください 
  - (プレビュー 5 の新機能) オブジェクト エクスプローラーでのデータベース サイズ ([サイズ (MB)]) の表示方法を修正/改善しました。つまり、小数点以下を 2 桁のみにし、桁区切り記号を使用して書式設定しました。 詳細については、 https://feedback.azure.com/forums/908035/suggestions/34379308 を参照してください
  - (プレビュー 5 の新機能) "空間インデックス" の作成が "このアクションを完了するには、プロパティ PartitionScheme を設定してください" のようなエラーで失敗する原因となっていた問題を修正しました。
  - (プレビュー 5 の新機能) オブジェクト エクスプローラーのパフォーマンスを若干改善して、可能な場合には、余分なクエリの発行を回避するようにしました。
  - (プレビュー 5 の新機能) データベースの名前を変更するときに、すべてのスキーマ オブジェクトに対して確認を要求するためのロジックが拡張されました (この設定は構成可能で、これは無効になっています)

- **ヘルプ ビューアー**
  - オンライン/オフライン モードの準拠に関するロジックを改善しました (対処が必要な問題がまだいくつかある可能性があります)
  - オンライン/オフライン設定に従うように [ヘルプの表示] を修正しました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791 を参照してください

- **オブジェクト スクリプト作成**
  - 全体的なパフォーマンスの改善: WideWorldImporters のスクリプト生成にかかる時間が、SSMS 17.7 と比べて半分になりました
  - オブジェクトのスクリプト作成時に、既定値がある DB のスコープ設定の構成は省略されています 
  - スクリプト作成時に動的 T-SQL を生成しないでください。詳細については、こちら (https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391) を参照してください
  - SQL Server 2016 以前のテーブルをスクリプト化するときに、"エッジとして" および "ノードとして" のグラフ構文を省略します。
  - MFA で AAD を使用して Azure SQL Database に接続している場合、データベース オブジェクトのスクリプト作成が失敗する問題が修正されました。
  - (プレビュー 6 の新機能) Azure SQL Database で GEOMETRY_AUTO_GRID/GEOGRAPHY_AUTO_GRID を使用して、空間インデックスのスクリプトを作成しようとしたときにエラーがスローされていた問題が修正されました。

- **テーブル デザイナー (Table Designer)**
  - (プレビュー 4 より前の新機能) "200 行の編集" 時のクラッシュを修正しました
  - Azure SQL Database に接続したときにデザイナーがテーブルを追加できていた問題を修正しました

- **SMO**
  - SMO/ServerConnection で SqlCredential ベースの接続が正しく行われない問題を修正しました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941 を参照してください
  - (プレビュー 6 の新機能) SMO を使用して作成されたアプリケーションで、複数のスレッドで同じサーバーのデータベースを列挙しようとした場合に、各スレッドで別の SqlConnection インスタンスを使用していてもエラーが発生していた問題が修正されました。

- **AS**
  - AS Xevent UI に対する [詳細設定] がクリップされてしまう問題を修正しました。
  - (プレビュー 5 の新機能) DAX の解析でファイルが見つからないことを示す例外がスローされる問題を修正しました
  - (プレビュー 5 の新機能) [スタート] メニューに "配置ウィザード" に戻るショートカットを追加しました

- **IS**
  - (プレビュー 5 の新機能) SQL Server 2019 と SSMS 18.0 が同じコンピューターにインストールされている場合、配置ウィザードで SQL Server への接続に失敗する、SxS の問題を修正しました。
  - (プレビュー 5 の新機能) メンテナンス プランの作成時に、メンテナンス プランのタスクを編集できない問題を修正しました。
  - (プレビュー 5 の新機能) 配置中のプロジェクトの名前が変更されると、配置ウィザードが停止する問題を修正しました。
  - (プレビュー 5 の新機能) Azure-SSIS IR のスケジュール機能での環境設定を有効にしました。

- **フラット ファイルのインポート ウィザード**
  - テーブルが既に存在する場合、フラット ファイルのインポートでターゲット テーブルを変更できない問題が修正されました。詳細については、こちら (https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186) を参照してください
  - "フラット ファイルのインポート ウィザード" で二重引用符が正しく処理されない (エスケープされない) 問題を修正しました。詳細については、こちら (https://feedback.azure.com/forums/908035/suggestions/32897998) を参照してください
  - (浮動小数点の異なる区切り文字を使用するロケールに対する) 浮動小数点型の不適切な処理に関する問題を修正しました。
  - 値が 0 または 1 のときのビットのインポートに関する問題を修正しました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535 を参照してください
  - 浮動小数点が null として入力された問題を修正しました。 

- **HADR / AG**
  - (プレビュー 5 の新機能) [可用性グループのフェールオーバー] ウィザードでロールが常に "解決中" と表示される問題を修正しました 
  - (プレビュー 5 の新機能) [AG ダッシュ ボード] で SSMS が切り捨ての警告を示していた問題を修正しました。

- **データ分類** 
  - 新規インストールでデータ分類の推奨事項部分が機能しない原因となった設定の問題を修正しました。
  - (プレビュー 6 の新機能) データ分類ウィンドウで分類を保存するときに、他のデータベースで別のデータ分類ウィンドウが開いている問題が修正されました。

- **DB のバックアップ/復元/アタッチ/デタッチ**
  - .mdf ファイルの物理ファイル名が元のファイル名と一致しない場合に、ユーザーがデータベースをアタッチできない問題を修正しました
  - SSMS で有効な復元プランを見つけられない問題、または最適ではない復元プランが見つかることがある問題を修正しました。 詳細については、 https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752 を参照してください。
  - URL バックアップを復元しようとしたときの SSMS のクラッシュを修正しました (これは前のプレビューでの問題の再発です)
  - (プレビュー 5 の新機能) [データベースのアタッチ] ウィザードで名前が変更されたセカンダリ ファイルが表示されない問題を修正しました。 現在は、ファイルが表示され、そのファイルについてのコメント ("見つかりません" など) が追加されています。 詳細については、 https://feedback.azure.com/forums/908035/suggestions/32897434 を参照してください

- **ジョブの利用状況モニター**
  - ジョブの利用状況モニター (フィルターあり) を使用中にクラッシュする問題を修正しました

- **Managed Instance のサポート**
  - Managed Instance のサポートの改善/調整: UI でサポートされていないオプションが無効になり、URL 監査ターゲットを処理するために [監査ログの表示] オプションが修正されました。
  - [スクリプトの生成とパブリッシュ] ウィザードでサポートされていない CREATE DATABASE 句のスクリプトが生成されます
  - CL インスタンスのライブ クエリ統計は無効になりました
  - [データベースのプロパティ] -> [ファイル] で ALTER DB ADD FILE が誤ってスクリプトされていました
  - 他のスケジュールの種類が選択されている場合でも、ONIDLE スケジュールが選択される SQL エージェント スケジューラによる回帰を修正しました
  - Azure Storage でバックアップを行う MAXTRANSFERRATE、MAXBLOCKSIZE の調整
  - RESTORE 操作の前にテール ログ バックアップがスクリプト化される問題 (これは CL ではサポートされていません)。
  - [データベースの作成] ウィザードで CREATE DATABASE ステートメントが正しくスクリプト化されない
  - マネージド インスタンスに接続するときに "利用状況モニター" を使用しようとしたときにエラーが表示される問題を修正しました。
  - (プレビュー 5 の新機能) (SSMS エクスプローラーでの) AAD ログインのサポートが強化されました。
  - (プレビュー 5 の新機能) SMO ファイル グループ オブジェクトのスクリプト作成が改善されました。
  - (プレビュー 5 の新機能) 資格情報と監査のための UI が改善されました。
  - (プレビュー 5 の新機能) 論理レプリケーションのサポートが追加されました。

- **Azure SQL Database**
  - Azure SQL DB でマスター データベースではなくユーザー データベースに接続したときに、Azure SQL DB クエリ ウィンドウにデータベース リストが正しく入力されない問題を修正しました。
  - SQL Azure DB に "テンポラル テーブル" を追加できない問題を修正しました。
  - (プレビュー 6 の新機能) Azure の [統計] メニューの下にある統計プロパティのサブメニュー オプションを有効にしました。これは、もうだいぶ前から完全にサポートされていたためです。
  - (50 を超える場合に) Azure サブスクリプションを表示できない一般的な Azure UI コントロールの問題を修正しました。 また、サブスクリプション ID ではなく名前による並べ替えに変更されました。 たとえば、URL からバックアップを復元するときに、ユーザーはこれを実行できます。
  - サブスクリプションを列挙するときに発生する一般的な Azure UI コントロールの問題を修正しました。この問題で "インデックスが範囲を超えています。 負でない値で、コレクションのサイズよりも小さくなければなりません" エラーがユーザーが一部のテナントについてサブスクリプションがない場合に表示されることがあります。 たとえば、URL からバックアップを復元するときに、ユーザーはこれを実行できます。

- **クエリ データ ストア**
  - (プレビュー 6 の新機能) "DocumentFrame (SQLEditors)" 例外がスローされる可能性がある問題が修正されました。
  - (プレビュー 6 の新機能) 組み込みのクエリ ストア レポートでカスタム時間間隔を設定しようとしたときに、ユーザーが開始/終了間隔で AM や PM を選択できなかった問題が修正されました

- **結果グリッド**
  - 高コントラスト モードの (選択された行番号が表示されない) 問題を修正しました。

- **XEvent プロファイラー**
  - 96 コアの SQL Server に接続したときに XEvent Profiler が起動できなかった問題を修正しました。

- **DAC インポート ウィザード**
  - (プレビュー 5 の新機能) AAD を使用して接続すると、DAC インポート ウィザードが動作しない問題を修正しました。

- **XEvent ビューアー**
  - (プレビュー 5 の新機能) "拡張イベントのツールバー オプション" を使用してイベントをグループ化しようとすると、XEvent ビューアーがクラッシュする問題を修正しました

- **脆弱性評価**
  - (プレビュー 5 の新機能) スキャン結果が適切に読み込まれない問題を修正しました。

- **データベース コピー ウィザード**
  - (プレビュー 6 の新機能) スクリプトの生成/転送/データベース コピー ウィザードでインメモリ テーブルを使用してテーブルを作成しようとすると、ansi_padding on が強制されません
  - (プレビュー 6 の新機能) SQL Server 2017 および SQL Server 2019 のデータベース転送タスク/データベース コピー ウィザードは壊れています
  - (プレビュー 6 の新機能) スクリプトの生成/転送/データベース コピー ウィザードでは、関連付けられている外部データ ソースが作成される前に、テーブルの作成がスクリプト化されます

- **Profiler**
  - (プレビュー 6 の新機能) Profiler イベントに "Aggregate Table Rewrite Query" イベントが追加されました。

- **プラン表示**
  - (プレビュー 6 の新機能) 複数のスレッドが存在する場合、新しい mem grant 演算子プロパティが正しく表示されません。

### <a name="deprecated-features"></a>非推奨の機能

次の機能は、SSMS で使用できなくなりました。

- T-SQL デバッガー
- データベース ダイアグラム
- OSQL.EXE
- 管理 UI の表示
- Configuration Manager ツール:
  - SQL Server Configuration Manager と Reporting Server Configuration Manager のどちらも SSMS セットアップに含まれなくなりました。

- DMF の標準ポリシー
  - SSMS でポリシーはインストールされなくなりました。 これらは Git に移動されます。 ユーザーは必要に応じてこれらを投稿し、ダウンロード/インストールすることができます。

- SSMS コマンド ライン オプション -P が削除されました
  - セキュリティに関する懸案事項で、コマンド ラインでクリア テキストのパスワードを指定するオプションが削除されました。

- [スクリプトの生成] | [Web サービスにパブリッシュ] が削除されました。 この (非推奨の) 機能は SSMS UI から削除されました。

- オブジェクト エクスプローラーでノード [メンテナンス] | [レガシ] が削除されました。 [スクリプトの生成とパブリッシュ] | [Web サービスに公開] オプションは削除されました。 *古い* "データベース メンテナンス プラン" と "SQL メール" ノードにはアクセスできなくなりました。 新しい [データベース メール] と [メンテナンス プラン] ノードは、引き続き通常どおり動作します。

### <a name="known-issues"></a>既知の問題

- .sql ファイルをダブルクリックすると SSMS が起動しますが、実際のスクリプトは開きません。
  - 回避策: .sql ファイルをドラッグし、SSMS エディターにドロップします。


## <a name="ssms-1791-latest-ga-release"></a>SSMS 17.9.1 (最新の GA リリース)

[SSMS 17.9.1](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409) ![のダウンロード](../ssdt/media/download.png)

- リリース番号:17.9.1<br>
- ビルド番号:14.0.17289.0<br>
- リリース日:2018 年 11 月 21 日

17.9.1 は 17.9 に対する小規模な更新であり、次のバグが修正されています。

- "Active Directory - Universal with MFA のサポート" 認証を SQL クエリ エディターと共に使用すると、クエリを呼び出すたびに接続が終了し、再び開かれることがある、という問題を修正しました。 接続が終了する副作用として、グローバル一時テーブルが予期せず削除されること、また場合によって接続に新しい SPID が付与されることがあります。
- 復元プランが復元プランを発見できない、または特定の条件下で非効率的な復元プランが生成されるという、長いあいだ未解決であった問題を修正しました。
- Azure SQL データベースへの接続時にエラーが発生する原因であった "データ層アプリケーションのインポート" ウィザードでの問題を修正しました。



> [!NOTE]
> SSMS 17.x の英語以外のローカライズされたリリースでは、次のものにインストールする場合、[KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/kb/2862966)が必要です:Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2。

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40a)








## <a name="ssms-179"></a>SSMS 17.9

[SSMS 17.9](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409) ![のダウンロード](../ssdt/media/download.png)

ビルド番号:14.0.17285.0<br>
リリース日:2018 年 9 月 4 日

> [!NOTE]
> SSMS 17.x の英語以外のローカライズされたリリースでは、次のものにインストールする場合、[KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/kb/2862966)が必要です:Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2。

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40a)


### <a name="whats-new"></a>新機能

**SSMS 全般**


プラン表示:

- グラフィカルなプラン表示で、特定のプランに対してこの機能をアクティブ化したときに、新しい行モード メモリ許可フィードバックの属性が表示されるようになりました。IsMemoryGrantFeedbackAdjusted と LastRequestedMemory が MemoryGrantInfo クエリ プランの XML 要素に追加されます。 行モード メモリ許可フィードバックについて詳しくは、「[Microsoft SQL データベースでのアダプティブ クエリの処理](https://docs.microsoft.com/sql/relational-databases/performance/adaptive-query-processing)」を参照してください。

Azure SQL: 

- Azure DB の作成に仮想コア SKU のサポートが追加されました。 詳細については、「[仮想コアベースの購入モデル](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers#vcore-based-purchasing-model)」を参照してください。
 

### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**
    
レプリケーション モニター:

- レプリケーション モニター (SqlMonitor.exe) が起動しない原因となっていた問題を修正しました (User Voice の項目: https://feedback.azure.com/forums/908035-sql-server/suggestions/34791079)。

フラット ファイルのインポート ウィザード:

- "フラット ファイル ウィザード" ダイアログのヘルプ ページへのリンクを修正しました 
- テーブルが既に存在しているときにウィザードでターゲット テーブルを変更できない問題を修正しました。これによってユーザーは、ウィザードを終了して失敗したテーブルを削除してから改めてウィザードに情報を入力することなく、再試行できるようになりました (User Voice の項目: https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186)。

データ層アプリケーションのインポート/エクスポート:

- .bacpac のインポートが、"Error SQL72014: .Net SqlClient Data Provider: メッセージ 9108、レベル 16、状態 10、行 1 この種の統計では増分がサポートされていません"のようなメッセージと共に失敗する場合があることの原因となっていた (DacFx の) 問題を修正しました。 この問題は、パーティションが定義されていてテーブルにインデックスが付いていないテーブルを扱うときに発生しました。

IntelliSense:

- MFA で AAD を使用する場合に Intellisense の入力候補が動作しなかった問題を修正しました。

オブジェクト エクスプローラー:

- "フィルター ダイアログ" が、SSMS を稼働しているモニターではなくランダムなモニターに表示された問題を修正しました (マルチ モニター システム)。

Azure SQL:

- [使用できるデータベース] でデータベースが列挙されるときに、特定のデータベースに接続しているとドロップダウンに "master" が表示されなかった問題を修正しました。
- MFA で AAD を使用して Azure SQL Database に接続している場合、スクリプト ([データ] または [スキーマとデータ]) を生成しようとすると失敗した問題を修正しました。
- ビュー デザイナー (ビュー) において、Azure SQL Database に接続していると UI から [テーブルの追加] を選択できなかった問題を修正しました。
- MFA トークンの更新中に SSMS クエリ エディターによって接続が自動的に終了および再開された問題を修正しました。 これにより、ユーザーが気付かない副作用 (たとえば、トランザクションを終了して再開しない場合) の発生を回避できます。 この変更では、プロパティ ウィンドウにトークンの有効期限が追加されます。 
- MFA ログインでの AAD で、インポートされた MSA アカウントに対して SSMS でパスワード プロンプトが適用されなかった問題を修正しました。 

利用状況モニター: 

- SQL 認証を使用して利用状況モニターから起動した場合に [ライブ クエリ統計] がハングする原因となっていた問題を修正しました。 

Microsoft Azure との統合: 

- SSMS によって最初の 50 個のサブスクリプション (Always Encrypted のダイアログ、BACKUP TO URL または RESTORE FROM URL のダイアログなど) しか表示されない問題を修正しました。 
- (BACKUP TO URL または RESTORE FROM URL のダイアログで) ストレージ アカウントを持っていない Microsoft Azure アカウントにサインインしようとしているときに、SSMS によって例外 ("インデックスが範囲外") がスローされた問題を修正しました。 

オブジェクト スクリプト作成: 

- DROP および CREATE のスクリプトを作成するときに、SSMS によって動的 T-SQL が生成されなくなりました。
- データベース オブジェクトのスクリプトを作成するときに、SSMS によってデータベース スコープ構成を設定するスクリプトが (それらが既定値に設定されていれば) 生成されなくなりました。

Help:

- [ヘルプに関するヘルプ] でオンライン/オフライン モードが考慮されないという、長い間未解決だった問題を修正しました。
- [ヘルプ | コミュニティ プロジェクト && サンプル] をクリックすると、SSMS によって既定のブラウザーで Git ページが開かれるようになり、古いブラウザーの使用に関するエラーや警告が表示されなくなりました。

### <a name="known-issues"></a>既知の問題


> [!IMPORTANT]
> "*Active Directory - Universal with MFA のサポート*" 認証を SQL クエリ エディターと共に使用する場合、クエリを呼び出すたびに接続が終了し、再び開かれることがあります。 このような終了の副作用として、グローバル一時テーブルが予期せず削除されること、また場合によって接続に新しい SPID が付与されることがあります。 この終了は、接続上に開いているトランザクションがある場合には発生しません。 この問題を回避するために、ユーザーは接続パラメーターに `persist security info=true` を設定できます。




## <a name="previous-ssms-releases"></a>以前のリリースの SSMS

以前のバージョンの SSMS をダウンロードするには、次のセクションのタイトル リンクをクリックします。

## <a name="downloadssdtmediadownloadpng-ssms-1781httpsgomicrosoftcomfwlinklinkid875802"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.8.1](https://go.microsoft.com/fwlink/?linkid=875802)
*17.8 では SQL データベースのプロビジョニングに関連するバグが検出されたため、17.8 は SSMS 17.8.1 に置き換えられました。*

ビルド番号:14.0.17277.0<br>
リリース日:2018 年 6 月 26 日

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40a)


### <a name="whats-new"></a>新機能

**SSMS 全般**

データベースのプロパティ:

- このバージョンでは、ファイル グループ用の **AUTOGROW_ALL_FILES** 構成オプションが公開されます。 この新しい構成オプションは、[データベースのプロパティ] > [ファイル グループ] ウィンドウにおいて、使用可能なファイル グループ (ファイルストリーム ファイル グループとメモリ最適化ファイル グループを除く) ごとにチェック ボックスの新しい列 ([すべてのファイルを自動拡張]) の形式で追加されます。 ユーザーは、対応する [すべてのファイルを自動拡張] チェック ボックスをオン/オフにすることで、特定のファイル グループに対して AUTOGROW_ALL_FILES を有効/無効にすることができます。 それに応じて、CREATE 用のデータベースのスクリプト化またはデータベース (SQL 2016 以上) 用のスクリプトの生成の際に、**AUTOGROW_ALL_FILES** オプションが適切にスクリプト化されます。
    
SQL エディター:

- ユーザーにマスターへのアクセス権がない場合の、Azure SQL Database における Intellisense のエクスペリエンスが向上しました。

スクリプトの作成:

- 全般的な (特に、待機時間の長い接続における) パフォーマンスが向上しました。
    
**Analysis Services (AS)**

- Analysis Services クライアント ライブラリとデータ プロバイダーが最新バージョンに更新され、新しい Azure Government AAD 権限 (login.microsoftonline.us) のサポートが追加されました。



### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**
    
メンテナンス プラン:

- SQL 認証を使用するメンテナンス プランを編集する場合に "オペレーターへの通知タスク" が失敗していた問題を修正しました。
    
スクリプトの作成:

- SMO における PostProcess アクションによってリソースが消費され、SQL ログインが失敗する問題を修正しました。
    
SMO:

- 既定の制約を含む列を追加する際にデータが既にテーブルに存在すると Table.Alter() が失敗する問題を修正しました。 詳細については、「[sql server smo generating inline default constraint when adding a column to a table containing data](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895625)」 (データを含むテーブルに列を追加する際に SQL Server SMO がインラインの既定の制約を生成する) を参照してください。
    
Always Encrypted:

- パーティション テーブルで Always Encrypted を有効にした場合のロック タイムアウト エラーの原因となっていた (DacFx の) 問題を修正しました。
    

**Analysis Services (AS)**

- 表形式 Analysis Services 1400 レベルの互換性モデルの OAuth データ ソースを変更する場合に発生していた問題を修正しました。この問題が原因で、OAuth トークンにおける変更がデータ ソースで更新されませんでした。
- Analysis Services 表形式 1400 レベルの互換性モデルにおける一部の無効なデータ ソースの資格情報の使用時または Power Query (Oracle など) での [データ ソースの変更] の移行をサポートしていないデータ ソースの編集時に発生する可能性のあった SSMS のクラッシュを修正しました。


### <a name="known-issues"></a>既知の問題

- *[プロパティ]* ウィンドウでファイル グループのプロパティを変更した後に *[スクリプト]* ボタンをクリックすると、2 つのスクリプトが生成されます。1 つ目は *USE<database>* ステートメントを使用したスクリプト、2 つ目は *USE master* ステートメントを使用したスクリプトです。  *USE master* を使用したスクリプトの生成時にはエラーが発生するため、このスクリプトを破棄する必要があります。 *USE <database>* ステートメントを含むスクリプトを実行してください。
- 新しい *General Purpose* または *Business Critical* エディションの Azure SQL Database を使用するとき、無効なエディションであるというエラーが一部のダイアログに表示されます。
- XEvent ビューアーで待機時間が発生する場合があります。 これは、[.NET Framework における既知の問題](https://github.com/Microsoft/dotnet/blob/master/releases/net472/dotnet472-changes.md#sql)です。 NetFx 4.7.2 へのアップグレードを検討してください。




## <a name="downloadssdtmediadownloadpng-ssms-177httpsgomicrosoftcomfwlinklinkid873126"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.7](https://go.microsoft.com/fwlink/?linkid=873126)

ビルド番号:14.0.17254.0<br>
リリース日:2018 年 5 月 9 日

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40a)


### <a name="whats-new"></a>新機能

**SSMS 全般**

レプリケーション モニター:   
- レプリケーション モニターでは、パブリッシャー データベースかディストリビューター データベースが可用性グループに含まれるとき、リスナーを登録できるようになりました。 パブリッシャー データベースかディストリビューター データベースが AlwaysOn 可用性グループに含まれるとき、レプリケーション環境を監視できるようになりました。 
 
Azure SQL Data Warehouse: 
- Azure SQL Data Warehouse で外部テーブルの "拒否された行の場所" サポートを追加します。 

**Integration Services (IS)**

- Azure SQL Database にデプロイされた SSIS パッケージのスケジュールを設定する機能を追加しました。 SQL Server エージェントがファーストクラス ジョブ スケジューラーとして使用されていたオンプレミス SQL Server や SQL Database Managed Instance とは異なり、SQL Database にはスケジューラーが組み込まれていません。 この新しい SSMS 機能は SQL Server エージェントに似た、おなじみのインターフェイスを備えており、SQL Database にデプロイされているパッケージをそのインターフェイスでスケジュール設定できます。 SQL Database を使用して SSIS カタログ データベース (SSISDB) をホストする場合、この SSMS 機能を使用し、SSIS パッケージのスケジュール設定に必要なデータ ファクトリのパイプライン、アクティビティ、トリガーを生成できます。 その後、データ ファクトリでそれらのオブジェクトを編集したり、拡張したりできます。 詳細については、[SSMS を使用する Azure SQL Database での SSIS パッケージの実行のスケジュール設定](../integration-services/lift-shift/ssis-azure-schedule-packages-ssms.md)に関するページを参照してください。 Azure Data Factory のパイプライン、アクティビティ、トリガーの詳細については、「[Azure Data Factory のパイプラインとアクティビティ](https://docs.microsoft.com/azure/data-factory/concepts-pipelines-activities)」と「[Azure Data Factory でのパイプラインの実行とトリガー](https://docs.microsoft.com/azure/data-factory/concepts-pipeline-execution-triggers)」を参照してください。
- SQL Managed Instance の SQL エージェントで SSIS パッケージのスケジュール設定をサポート マネージド インスタンスで SSIS パッケージを実行する SQL エージェント ジョブを作成できるようになりました。 

### <a name="bug-fixes"></a>バグの修正

**SSMS 全般** 

メンテナンス プラン:   
- 既存のメンテナンス プランのスケジュールを変更しようとすると例外がスローされる問題を解決しました。 詳細については、「[SSMS 17.6 crashes when clicking on a schedule in a maintenance plan](https://feedback.azure.com/forums/908035-sql-server/suggestions/33712924)」 (メンテナンス プランでスケジュールをクリックすると、SSMS 17.6 がクラッシュする) を参照してください。

Always On: 
- Always On Latency Dashboard と SQL Server 2012 が連動しない問題を解決しました。
 
スクリプトの作成: 
- 管理者以外のユーザーが Azure SQL Data Warehouse に対するストアド プロシージャを作成できない問題を解決しました。
- Azure SQL Database に対してデータベースのスクリプトを作成するとき、*SCOPED CONFIGURATION* プロパティのスクリプトが作成されなかった問題を解決しました。
 
テレメトリ: 
- SSMS がクラッシュし、テレメトリの送信を無効にした後、サーバーに接続を試行する問題を解決しました。
 
Azure SQL Database: 
- ユーザーが互換性レベルを設定または変更できない問題を解決しました (ドロップダウン フォームが空)。 注: 互換性レベルを 150 に設定するには、*[スクリプト]* ボタンを使用し、スクリプトを手動で編集する必要があります。 
 
SMO: 
- SMO でエラー ログ サイズ設定を公開しました。 詳細については、「[Set the Maximum Size of the SQL Server Error Logs](https://feedback.azure.com/forums/908035-sql-server/suggestions/33624115)」 (SQL Server エラー ログの最大サイズの設定) を参照してください。  
- Linux の SMO でラインフィード スクリプト作成を修正。
- 滅多に使用されないプロパティを取得するときのさまざまなパフォーマンスを改善。  

IntelliSense: 
- パフォーマンス改善: 列データに関して、IntelliSense クエリの量減らしました。 これは特に、大量の列があるテーブルの利用時に効果があります。 

SSMS ユーザー設定:
- オプション ページのサイズが正しく変更されない問題を解決しました。

その他:  
- "*統計詳細*" ページのテキスト表示を改善しました。 

**Integration Services (IS)**

- Azure SQL Database Managed Instance のサポートが改善しました。
- ユーザーが SQL Server 2014 以前のカタログを作成できない問題を解決しました。
- レポートに関する 2 つの問題を解決しました。
   - Azure サーバーのコンピューター名を削除しました。
   - ローカライズされたオブジェクト名の処理を改善しました。


### <a name="known-issues"></a>既知の問題

新しい *General Purpose* または *Business Critical* エディションの Azure SQL Database を使用するとき、無効なエディションであるというエラーが一部のダイアログに表示されます。

## <a name="downloadssdtmediadownloadpng-ssms-176httpsgomicrosoftcomfwlinklinkid870039"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.6](https://go.microsoft.com/fwlink/?linkid=870039)

ビルド番号:14.0.17230.0<br>
リリース日:2018 年 3 月 20 日

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40a)

### <a name="whats-new"></a>新機能

**SSMS 全般**

SQL Database Managed Instance:

- [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) のサポートが追加されました。 Azure SQL Database Managed Instance は、SQL Server オンプレミスとのほぼ 100% の互換性、セキュリティに関する一般的な問題に対応するネイティブな[仮想ネットワーク (VNet)](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) の実装、およびオンプレミスの SQL Server ユーザーに適した[ビジネス モデル](https://azure.microsoft.com/pricing/details/sql-database/)を提供します。
- 次のような一般的な管理シナリオをサポートします。
   - データベースの作成と変更。
   - データベースのバックアップと復元を行う。
   - データ層アプリケーションのインポート、エクスポート、抽出、公開。
   - サーバー プロパティの表示と変更。
   - オブジェクト エクスプローラーの完全なサポート。
   - データベース オブジェクトのスクリプト作成。
   - SQL エージェント ジョブのサポート。
   - リンク サーバーのサポート。
- マネージド インスタンスの詳細については、[こちら](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/)を参照してください。

オブジェクト エクスプローラー:
- オブジェクト エクスプローラーからクエリ ウィンドウにドラッグ アンド ドロップするときに、名前を角かっこで囲むことを強制しない設定が追加されました。 (ユーザー提案 [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933) および [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051))

データ分類:
- 一般的な機能強化とバグの修正。

**Integration Services (IS)**

- [SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) にパッケージを展開するサポートが追加されました。

### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**

データ分類:

- 新しく追加した分類が古い*情報の種類*と*秘密ラベル*で表示される *データ分類の問題を修正しました。
- 大文字と小文字を区別する照合順序に設定されたサーバーを対象とすると "*データ分類*" が動作しなかった問題を修正しました。
        
Always On:

- 大文字と小文字を区別する照合順序にサーバーが設定されているときに *[待機時間データの収集]* をクリックするとエラーになる、AG のダッシュボードの表示の問題を修正しました。
- クラスター サービスのシャットダウン時に AG が "*分散*" と誤って報告される SSMS の問題を修正しました。
- *[可用性グループの作成]* ダイアログを使って AG を作成するときに *ReadOnlyRoutingUrl* が要求される問題を修正しました。
- プライマリがダウンしたときに手動でセカンダリにフェールオーバーすると NullReferenceException がスローされる問題を修正しました。
- バックアップ/復元を使って可用性グループを作成してデータベースを初期化すると、セカンダリ レプリカでデータベース ファイルが既定のディレクトリに作成される問題を修正しました。 次の修正が含まれます。
   - データ/ログ ディレクトリ検証コントロールを追加します。
   - レプリカがプライマリ レプリカと異なる OS 上にある場合にのみファイルの再配置を行います。
- SSMS ウィザードが *CLUSTER_TYPE* オプションを生成しないためにセカンダリの結合が失敗する問題を修正しました。

セットアップ:
- SSMS が既定以外の場所にインストールされていた場合、"アップグレード パッケージ" をインストールすることによって SSMS をアップグレードしようとすると失敗する問題を修正しました。

SMO:
- SQL Server 2016 以降でテーブルのスクリプトに最大 30 秒かかるパフォーマンスの問題を修正しました (今では、1 秒未満に短縮されています)。

オブジェクト エクスプローラー:
- オブジェクト エクスプローラーで "*管理*" ノードを展開しようとすると SSMS が "オブジェクトを DBNull から他のタイプにキャストすることはできません" のような例外をスローする問題を修正しました。
- ユーザー定義の PS プロファイルが出力を生成すると "*PowerShell の起動*" が SQLServer モジュールを検出しない問題を修正しました。
- オブジェクト エクスプローラーでテーブルまたはインデックス ノードを右クリックすると発生した断続的なハングを修正しました。

データベース メール:
- 16 個より多いプロファイルを表示/管理しようとすると "*データベース メール構成ウィザード*" が例外をスローする問題を修正しました。


**Analysis Services (AS)**

- SSMS で 1400 互換性レベル モデルのデータ ソースを変更すると変更がサーバーに保存されない問題を修正しました。

**Integration Services (IS)**

- SQL Database Managed Instance に接続すると SSMS で SSIS カタログ ノードとレポートが表示されない問題を修正しました

### <a name="known-issues"></a>既知の問題

> [!WARNING]
> [メンテナンス プラン](../relational-databases/maintenance-plans/maintenance-plans.md)の使用中に SSMS 17.6 が不安定になりクラッシュするという既知の問題があります。 メンテナンス プランを使用する場合は、SSMS 17.6 をインストールしないでください。 17.6 を既にインストールしていて、この問題の影響を受けている場合は、SSMS 17.5 にダウングレードしてください。 



## <a name="downloadssdtmediadownloadpng-ssms-175httpsgomicrosoftcomfwlinklinkid867670"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.5](https://go.microsoft.com/fwlink/?linkid=867670)
一般公開 | ビルド番号:14.0.17224.0

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40a)

### <a name="whats-new"></a>新機能

**SSMS 全般**

データの検出と分類:

- データベース内の機密データの検出、分類、ラベル付けとレポート作成を行うための新しい SQL データの検出と分類機能が追加されました。 
- 最も機密性の高いデータ (ビジネス、財務、医療、個人データなど) の自動検出と分類は、組織の情報保護の達成において極めて重要な役割を果たすことができます。
- 詳細については、「[SQL データの検出と分類](../relational-databases/security/sql-data-discovery-and-classification.md)」を参照してください。

クエリ エディター:

- Azure SQL DW の区切られたテキストの外部ファイル形式に SkipRows オプションのサポートが追加されました。 この機能では、ユーザーは区切られたテキスト ファイルを SQL DW に読み込む際に指定した数の行をスキップすることができます。 また、FIRST_ROW キーワードの対応する intellisense/SMO サポートも追加されました。 

Showplan:

- SQL Data Warehouse の推定プラン ボタンを表示できるようになりました。
- 新しい showplan 属性 *EstimateRowsWithoutRowGoal* が追加され、*QueryTimeStats* に新しい showplan 属性 (*UdfCpuTime* と *UdfElapsedTime*) が追加されました。 詳細については、「[Optimizer row goal information in query execution plan added in SQL Server 2017 CU3](https://support.microsoft.com/help/4051361)」 (SQL Server 2017 CU3 で追加されたクエリ実行プランのオプティマイザー行の目標情報) を参照してください。



### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**

Showplan:

- LQS 接続の経過時間ではなく、エンジンの実行時間を表示するように、ライブ クエリ統計経過時間が修正されました。
- Showplan で GbApply や InnerApply などの Apply 論理演算子を認識できないという問題が修正されました。
- ExchangeSpill に関する問題が修正されました。

クエリ エディター:

- 先頭に "SET SHOWPLAN_ALL ON" が付いた単純なクエリを実行する際に SSMS が "入力文字列の形式が正しくありません。 (mscorlib)" というようなエラーをスローするという SPID に関する問題が修正されました。 


SMO:

- サーバーの照合順序で大文字と小文字が区別される場合に SMO が AvailabilityReplica プロパティをフェッチできない (その結果、SSMS で "マルチパート識別子 "a.delimited" をバインドできませんでした" というようなエラー メッセージが表示される場合がある) という問題が修正されました。
- 照合順序が処理されない (その結果、照合順序の大文字と小文字が区別されるサーバーで実行されているデータベースで右クリックしたときに、トルコ語のロケールの ma マシン上で実行されている SSMS で "レガシカーディナリティ推定が有効なスコープ構成ではありません" というようなエラーが表示される場合がある) という、DatabaseScopedConfigurationCollection クラスの問題が修正されました。
- SMO が SQL 2005 サーバーで SQL エージェント プロパティをフェッチできない (その結果、SSMS が "ローカル変数に既定値を代入できません。 スカラー変数 "\@ServiceStartMode を宣言してください" というようなエラーをスローし、最終的にオブジェクト エクスプローラーで SQL エージェント ノードが表示されない) という、JobServer クラスの問題が修正されました。

テンプレート: 

- "データベース メール": 2 つの誤字を修正しました [(https://feedback.azure.com/forums/908035/suggestions/33143512)](https://feedback.azure.com/forums/908035/suggestions/33143512)。  

オブジェクト エクスプローラー:
- インデックスの管理圧縮が失敗する問題を修正しました (https://feedback.azure.com/forums/908035-sql-server/suggestions/32610058-ssms-17-4-error-when-enabling-page-compression-o)。

監査: 
- *監査ファイルの統合*機能に関する問題が修正されました。
<br>

### <a name="known-issues"></a>既知の問題

データ分類:
- 分類を削除してから、同じ列の新しい分類を手動で追加すると、古い情報の種類と機密ラベルがメイン ビューの列に割り当てられます。<br>
*回避策*:分類をメイン ビューに戻した後、保存する前に新しい情報の種類と機密ラベルを割り当てます。


## <a name="downloadssdtmediadownloadpng-ssms-174httpsgomicrosoftcomfwlinklinkid864329"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.4](https://go.microsoft.com/fwlink/?linkid=864329)
一般公開 | ビルド番号:14.0.17213.0

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40a)


### <a name="whats-new"></a>新機能

**SSMS 全般**

脆弱性評価:
- データベースをスキャンして潜在的な脆弱性およびベスト プラクティスからの逸脱 (構成の不備、過剰なアクセス許可、公開された機密データなど) がないかを確認できるように新しい SQL 脆弱性評価サービスが追加されました。 
- 評価の結果には、各々の問題を解決する実践的な手順が含まれ、カスタマイズした修復スクリプトが適宜提供されます。 評価レポートは環境ごとにカスタマイズし、特定の要件に合わせて調整することができます。 詳細については、「[SQL 脆弱性評価](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment)」を参照してください。

SMO:
- Azure 上で *HasMemoryOptimizedObjects が例外をスローする問題を修正しました。
- 新しい CATALOG_COLLATION 機能のサポートが追加されました。

Always On ダッシュボード:
- 可用性グループでの待機時間の分析の機能強化。
- 2 つの新しいレポート(*AlwaysOn\_Latency\_Primary* および *AlwaysOn\_Latency\_Secondary*) が追加されました。

Showplan:
- 適切なドキュメントを指すようにリンクが更新されました。
- 実際に作成されたプランから直接、単一プラン分析を実行できます。
- 新しいアイコンのセット。
- GbApply や InnerApply などの "Apply 論理演算子" を認識するためのサポートが追加されました。
        
XE プロファイラー:
- XEvent プロファイラーに名前が変更になりました。
- 既定で、[停止] / [開始] メニュー コマンドによってセッションが停止/開始されるようになりました。
- キーボード ショートカットが有効になりました (たとえば、検索する場合は CTRL + F キー)。
- XEvent プロファイラー セッションの適切なイベントに database\_name アクションと client\_hostname アクションが追加されました。 変更を有効にするために、サーバー上で既存の QuickSessionStandard セッション インスタンスまたは QuickSessionTSQL セッション インスタンスを削除することが必要な場合があります - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)

コマンド ライン:
- 新しいコマンド ライン オプション ("-G") が追加されました。このオプションを指定すると、Active Directory 認証 ('統合' または 'パスワード' のいずれか) を使用してサーバー/データベースへの SSMS の自動接続を行うことができます。 詳細については、「[Ssms ユーティリティ](ssms-utility.md)」を参照してください。

フラット ファイルのインポート ウィザード:
- テーブルの作成時に既定値 ("dbo") 以外のスキーマの名前を選択する方法が追加されました。

クエリ ストア:
- クエリ ストアで使用可能なレポート リストを展開するときの "低下したクエリ" レポートが復元されました。

**Integration Services (IS)**
- 展開ウィザードにパッケージ検証機能が追加されました。これにより、ユーザーは、Azure SSIS IR でサポートされていない SSIS パッケージ内のコンポーネントを容易に確認することができます。

### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**

- オブジェクト エクスプローラー:データベース スナップショットでテーブル値関数ノードが表示されないという問題を修正しました - [Connect 3140161](https://connect.microsoft.com/SQLServer/feedback/details/3140161)です。
サーバーが autoclose データベースがある場合に、"*データベース*" ノードを展開する際のパフォーマンスが向上しました。
- クエリ エディター:マスター データベースへのアクセス権をユーザーが持っていない場合に IntelliSense が失敗するという問題を修正しました。
リモート コンピューターへの接続を終了するときに、場合によって SSMS をクラッシュさせていた問題を修正しました - [Connect 3142557](https://connect.microsoft.com/SQLServer/feedback/details/3142557)。
- XEvent ビューアー:XEL へのエクスポート機能が再び有効になりました。
場合によって、ユーザーが XEL ファイル全体を読み込めないという問題を修正しました。
- XEvent プロファイラー:ユーザーが *VIEW SERVER STATE* アクセス許可を持っていない場合に SSMS のクラッシュの原因となっていた問題を修正しました。
XE プロファイラー ライブ データ ウィンドウを閉じても基になるセッションが停止しないという問題を修正しました。
- 登録済みサーバー:[... に移動] コマンドが停止する問題を修正しました ([Connect 3142862](https://connect.microsoft.com/SQLServer/feedback/details/3142862) および [Connect 3144359](https://connect.microsoft.com/SQLServer/feedback/details/3144359/))。
- SMO:転送オブジェクトの TransferData メソッドが動作していないという問題を修正しました。
SQL DW データベースが一時停止した場合に Server データベースが例外をスローするという問題を修正しました。
SQL Data Warehouse に対して SQL データベースをスクリプト化すると、不適切な T-SQL パラメーター値が生成されるという問題を修正しました。
DB の拡張をスクリプト化したときに *DATA\_COMPRESSION* オプションが正しく送信されないという問題を修正しました。
- ジョブの利用状況モニター:ユーザーがカテゴリによるフィルター処理を試みているときに "インデックスが範囲を超えています。 負でない値で、コレクションのサイズよりも小さくなければなりません。 
      パラメーター名: インデックス (System.Windows.Forms)" というエラーが発生するという問題を修正しました - [Connect 3138691](https://connect.microsoft.com/SQLServer/feedback/details/3138691)。
- 接続ダイアログ:読み取り/書き込みドメイン コントローラーへのアクセス権を持たないドメイン ユーザーは、SQL 認証を使用して SQL Server にログインできないという問題を修正しました - [Connect 2373381](https://connect.microsoft.com/SQLServer/feedback/details/2373381)。
- レプリケーション:SQL Server でプル サブスクリプションのプロパティを参照するときに、エラー "値 'null' をプロパティ ServerInstance に適用できません" が表示されるという問題を修正しました。
- SSMS セットアップ:SSMS セットアップが原因で、コンピューター上にインストールされている一部の製品が正しく再構成されないという問題を修正しました。
- ユーザー設定:
   - この修正プログラムにより、Azure Government ユーザーは、ユニバーサル認証と Azure Active Directory ログインを介して SSMS で Azure SQL Database および Azure Resource Manager リソースに中断されることなくアクセスできます。  SSMS の以前のバージョンのユーザーの場合は、[ツール]、[オプション]、[Azure サービス] の順に開き、[リソース管理] で "Active Directory Authority" プロパティの構成を https://login.microsoftonline.us に変更する必要があります。

**Analysis Services (AS)**

- プロファイラー: Window 認証を使用して Azure AS に対する接続を試みるときに発生する問題を修正しました。
- 1400 モデル上で接続の詳細をキャンセルするときにクラッシュを引き起こす可能性のある問題を修正しました。
- 資格情報を更新するときに、接続プロパティ ダイアログで Azure BLOB キーを設定すると、それが視覚的にマスクされるようになります。
- Azure Analysis Services のユーザー選択ダイアログで、検索時にオブジェクト ID ではなくアプリケーション ID guid が表示される問題を修正しました。
- データベース\MDX クエリ デザイナー ツールバーで、いくつかのボタンにアイコンが正しくマップされない原因となっていた問題を修正しました。
- msmdpump IIS http/https アドレスを使用した SSAS への接続を妨げる問題を修正しました。
- Azure Analysis Services の[ユーザー ピッカー] ダイアログ内の複数の文字列が新たに他の言語にも翻訳されました。
- MaxConnections プロパティが表形式モデルのデータ ソースに表示されるようになりました。
- 配置ウィザードで、Azure AS ロール メンバーに対する適切な JSON 定義が生成されるようになります。
- Azure AS に対して Windows 認証を選択した場合にログインを求めるメッセージが引き続き表示されるという SQL Profiler での問題を修正しました。



## <a name="downloadssdtmediadownloadpng-ssms-173httpsgomicrosoftcomfwlinklinkid858904"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.3](https://go.microsoft.com/fwlink/?linkid=858904)
一般公開 | ビルド番号:14.0.17199.0

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)


### <a name="enhancements"></a>機能強化

- インテリジェントなフレームワークを使用して、CSV ファイルのインポート エクスペリエンスを効率化するための新しい "フラット ファイルのインポート" ウィザードが追加されました。これは最小限のユーザーの介入または特殊なドメインの知識で使用できます。 詳細については、「[Import Flat File to SQL Wizard](../relational-databases/import-export/import-flat-file-wizard.md)」 (フラット ファイルを SQL ウィザードにインポートする) を参照してください。
- オブジェクト エクスプローラーに "XEvent プロファイラー" ノードが追加されました。 詳細については、「[SSMS XEvent Profiler の使用](../relational-databases/extended-events/use-the-ssms-xe-profiler.md)」を参照してください。
- パフォーマンス ダッシュボードでの待機の履歴レポートの待機のフィルター処理と分類を更新しました。
- "Predict" 関数の構文チェックを追加しました。
- 外部ライブラリ管理のクエリの構文チェックを追加しました。
- 外部ライブラリ管理の SMO サポートを追加しました。
- [登録済みサーバー] ウィンドウに [PowerShell の起動] のサポートを追加しました (新しい SQL PowerShell モジュールが必要)。
- Always On: 可用性グループに[読み取り専用ルーティングのサポート](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)を追加しました。
- [Active Directory - MFA で汎用のサポート] ログインの出力ウィンドウにトレースの詳細を送信するオプションを追加しました (既定ではオフになっているため、[ツール] > [オプション] > [Azure サービス] > [Azure クラウド] > [ADAL 出力ウィンドウのトレース レベル] の下にあるユーザー設定で有効にする必要があります)。 
- クエリ ストア: 
  - クエリ ストア UI は、QDS が何らかのデータを記録している限り、QDS がオフになっている場合でもアクセスできます。
  - クエリ ストア UI で、既存レポートのすべての待機の分類法が公開されるようになりました。 これにより、顧客が上位の待機中のクエリのシナリオのロック解除などができるようになります。
- [スクリプト パラメーター ヘッダーを含める] がオプションになりました (既定で無効になっており、[ツール] > [オプション] > [SQL Server オブジェクト エクスプローラー] > [スクリプト] > [スクリプト パラメーター ヘッダーを含める] の下のユーザー設定で有効にすることができます) - [Connect アイテム 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199)。
- "RC" ブランド化を削除しました。

### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**

- XEvent: 
   - SSMS が .xel ファイル内のイベントの一部だけを開く問題を修正しました。
   - 既定のデータベースが "master" でない場合の "ライブ データの監視" のエクスペリエンスが向上しました ([Connect 項目 1222582](https://connect.microsoft.com/SQLServer/feedback/details/1222582))。
- Always On:"ログ バックアップの復元" が "このバックアップ セットへのサインインは LSN x で終了します。これはデータベースに適用するには古すぎます" というエラーで失敗する可能性がある問題を修正しました。
- ジョブの利用状況モニター: 一貫性のないアイコンを修正しました。[Connect アイテム 3133100](https://connect.microsoft.com/SQLServer/feedback/details/3133100)
- クエリ ストア:クエリ ストア レポートでユーザーが "カスタム" の日付範囲を選択できない問題を修正しました。 以下の Connect アイテムにリンクされています。
   - [Connect アイテム 3139842](https://connect.microsoft.com/SQLServer/feedback/details/3139842)
   - [Connect アイテム 3139399](https://connect.microsoft.com/SQLServer/feedback/details/3139399)
- 保存されている情報に指定したデータベースがあり、ユーザーが既定値を選択した場合に、接続ダイアログで最近使用したデータベースが "クリア" されない問題を修正しました。
- オブジェクト スクリプト作成:ユーザーが DW データベースをサーバー上で一時停止したが、別の非 DW データベースを選択してそれをスクリプト作成しようとした場合に、"データベース スクリプトの生成" が機能せず、エラーがスローされる問題を修正しました。
スクリプト作成したストアド プロシージャのヘッダーがスクリプトの設定と一致せず、誤解を招くスクリプトになる問題を修正しました ([Connect アイテム 3139784](https://connect.microsoft.com/SQLServer/feedback/details/3139784))。
SQL Azure オブジェクトをターゲットにしたときに、"スクリプト ボタン" が再度有効になります。
  Azure SQL データベースに接続しているときに、一部のオブジェクト (UDF、ビュー、SP、トリガー) で "Alter" または "Execute" のスクリプト作成が許可されない SSMS の問題を修正しました ([Connect アイテム 3136386](https://connect.microsoft.com/SQLServer/feedback/details/3136386))。
- クエリ エディター:
  - Azure SQL Database をターゲットにする際の IntelliSense が向上しました。
  - 有効期限が切れた認証トークン (ユニバーサル認証) によりクエリが失敗する問題を修正しました。
  - Azure SQL Database に対して作業を行うときの IntelliSense が向上しました (特に、Azure SQL Database の接続時には、最新の T-SQL 文法 (140) が使用されます)。
  - サーバー上の DataWarehouse 以外のデータベースへの接続でクエリ ウィンドウを開くと、そのサーバーの DataWarehouse データベースへの後続のクエリ ウィンドウのすべてで、サポートされない型/オプションに関するさまざまなエラーがスローされます。
- Always On:
   - Always On ダッシュボードと AG プロパティ ページにシード処理モード列が追加されました。
   - プライマリが Windows にある場合に、Linux AG が作成できない問題を修正しました。[Connect アイテム 3139856](https://connect.microsoft.com/SQLServer/feedback/details/3139856)
- クエリ実行時の SSMS での複数の "メモリ不足" 問題を修正しました。[Connect アイテム 2845190](https://connect.microsoft.com/SQLServer/feedback/details/2845190)、[Connect アイテム 3123864](https://connect.microsoft.com/SQLServer/feedback/details/3123864)
- Profiler: 
   - SQL 2005 をターゲットとしたときに、Profiler が機能しない問題を修正しました。
   - Profiler が [サーバー証明書を信頼する] 接続オプションを受け入れない問題を修正しました。
- 利用状況モニター: Linux で実行されている SQL Server がポイントされた場合に利用状況モニターが機能しない問題を修正しました。
- 外部データ ソースまたは外部ファイル形式のオブジェクトを転送しない SMO 転送クラスの問題を修正しました。これらの種類のオブジェクトは、正しく転送に含まれるようになりました。
- 登録済みサーバー:
   - UA サーバーに対してマルチサーバー クエリが有効になりました (グループ内のすべての UA サーバーに対して同じトークンを使用しようとします)。
- AD ユニバーサル認証:
   - Azure AD 認証がサポートされない問題を修正しました。
   - テーブル/ビュー デザイナーが機能しない問題を修正しました。
   - "上位 1000 行を選択" と "上位 200 行を編集" が機能しない問題を修正しました。
- データベースの復元: ファイルを別の場所に移動したときに、パスの最後のフォルダーが復元で除外される問題を修正しました。
- 圧縮ウィザード:
   - インデックスの圧縮ウィザードの管理問題を修正しました。SQL 2016 以前のバージョンでデータの圧縮ウィザードが破損する問題を修正しました。
        https://connect.microsoft.com/SQLServer/feedback/details/3139342
   - Azure のテーブルとインデックスに圧縮ウィザードが追加されました。
- Showplan: 
   - PDW 演算子が認識されない問題を修正しました。
- サーバー プロパティ : 
   - サーバー プロセッサのアフィニティを変更できない問題を修正しました。


**Analysis Services (AS)**

- 1400 互換性レベルのテーブル モデルと Power Query データ ソースをサポートする展開ウィザードの多くの問題を修正しました。
- コマンド ラインから実行する際に、展開ウィザードで AS Azure に展開できるようになりました。
- AS Azure で Windows 認証を使用する際に、ユーザーがオブジェクト エクスプローラーでユーザー アカウントの名前を正しく確認できるようになりました。


### <a name="known-issues-in-this-173-release"></a>この 17.3 リリースの既知の問題:

**SSMS 全般**

- MFA を使用した UA を使用する Azure AD 認証では、次の SSMS 機能はサポートされていません。
   - データベース エンジン チューニング アドバイザーは Azure AD の認証ではサポートされていません。ユーザーに表示されるエラー メッセージが少しあいまいだという既知の問題があります。"Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,..." (ファイルまたはアセンブリ 'Microsoft.IdentityModel.Clients.ActiveDirectory を読み込めませんでした...) が、正常なメッセージである "Database Engine Tuning Advisor does not support Microsoft Azure SQL Database. (DTAClient) (Database Engine Tuning Advisor は Microsoft Azure SQL Database をサポートしていません(DTAClient)) の代わりに表示されます。
- DTA でクエリを分析しようとすると、次のエラーが発生します。"Object must implement IConvertible. (mscorlib)" (オブジェクトで IConvertible を実装する必要があります (mscorlib))。
- *[低下したクエリ]* がオブジェクト エクスプローラーのレポートのクエリ ストアのリストにありません。
   - 回避策:**[クエリ ストア]** ノードを右クリックし、**[View Regressed Queries]\(低下したクエリを表示します\)** を選択します。

**Integration Services (IS)**

- [catalog].[event_messagea] の [Execution_path] は、Scale Out でのパッケージの実行には正しくありません。[execution_path] は、パッケージの実行可能ファイルのオブジェクト名ではなく、"\Package" で開始します。 SSMS でパッケージ実行の概要レポートを表示すると、実行の概要の "実行パス" のリンクが機能しません。 回避策として、概要レポートの [メッセージの表示] をクリックして、すべてのイベント メッセージを確認します。


## <a name="downloadssdtmediadownloadpng-ssms-172httpsgomicrosoftcomfwlinklinkid854085"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.2](https://go.microsoft.com/fwlink/?linkid=854085)
一般公開 | ビルド番号:14.0.17177.0

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

### <a name="enhancements"></a>機能強化

- Multi-Factor Authentication (MFA)
  - 多要素認証を使用したユニバーサル認証 (UA with MFA) 向けの複数ユーザーの Azure AD 認証
  - 複数ユーザーの認証をサポートするため、MFA を使用したユニバーサル認証用に新しいユーザー資格情報の入力フィールドが追加されました。
- 接続ダイアログ ボックスで、次の 5 つの認証方法がサポートされるようになりました。
  - [Windows 認証]
  - SQL Server 認証 (SQL Server Authentication)
  - Active Directory - Universal with MFA のサポート
  - Active Directory - パスワード
  - Active Directory - 統合

- MFA を使用したユニバーサル認証を使用する DacFx のデータベースのインポート/エクスポート ウィザード。
- API のサポートについては、「[IUniversalAuthProvider インターフェイス](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx)」を参照してください。
- MFA を使用した Azure AD ユニバーサル認証で使用される ADAL マネージド ライブラリは、バージョン 3.13.9 にアップグレードされました。
- SQL Database および SQL Data Warehouse の Azure AD 管理者設定のサポートが実現された新しい CLI インターフェイスの追加。

 Active Directory の認証方法の詳細については、「[SQL Database と SQL Data Warehouse でのユニバーサル認証 (MFA 対応の SSMS サポート)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)」と「[SQL Server Management Studio 用に Azure SQL Database の多要素認証を構成する](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure)」を参照してください。

- 出力ウィンドウには、オブジェクト エクスプローラー ノードの展開時に実行されるクエリのエントリがあります。
- Azure SQL Databases のビュー デザイナーの有効化
- SSMS でのオブジェクトのスクリプト作成の既定のスクリプト作成オプションが、オブジェクト エクスプローラーから変更されました。
  - 以前は、新しいインストールには既定で、 SQL Server の最新バージョン (現時点では SQL Server 2017) を対象に生成されたスクリプトがありました。
  - SSMS 17.2 では、新しいオプションの *[スクリプト設定をソースに一致させる]* が追加されました。 *True* に設定すると、生成されるスクリプトは、オブジェクトがスクリプト化されるサーバーと同じバージョン、エンジンの種類、およびエンジンのエディションを対象にします。
  - [*スクリプト設定をソースに一致させる*] の値は既定で *True* に設定されているため、SSMS の新しいインストールは、オブジェクトのスクリプト作成を常に元のサーバーと同じターゲットにすることが自動的に既定値に設定されます。
  - [*スクリプト設定をソースに一致させる*] の値を *False* に設定すると、通常のスクリプトのターゲット オプションが有効になり、従来どおりに機能します。
さらに、すべてのスクリプト作成オプションが、独自のセクションの [*バージョン オプション*] に移動されました。 これらは [*全般スクリプト作成オプション*] の下にはありません。

- "Restore from URL" に National Clouds のサポートが追加されました。
- QueryStoreUI レポートで、sys.query_store_runtime_stats からの追加のメトリック (RowCount、DOP、CLR Time など) がサポートされるようになりました。
- Azure SQL Database で IntelliSense がサポートされるようになりました (https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases)
- セキュリティ: 接続ダイアログの既定値が、サーバー証明書を信頼せず、Azure SQL DB 接続の暗号化を要求することになります。
- SQL Server on Linux のサポートに関する全般的な改良点:
 - データベース メール ノードの復帰
 - パスに関連するいくつかの問題への対処
 - 利用状況モニターの安定性の向上
 - [接続プロパティ] ダイアログでの正しいプラットフォームの表示
- パフォーマンス ダッシュボード サーバー レポートを既定のレポートとして使用できるようになりました。
  - SQL Server 2008 以降のバージョンに接続できます。
  - 欠落したインデックスのサブレポートは、最も有用なインデックスを特定しやすくするため、スコアリングを使用します。
  - 履歴待機統計サブレポートで、待機の集計がカテゴリ別になりました。 アイドル状態とスリープの待機は既定で除外されます。
  - 新しい履歴ラッチ サブレポート。
- Showplan ノードの検索では、プランのプロパティを検索できます。 テーブル名などの任意の演算子プロパティを簡単に検索できます。 プランを表示しているときに、このオプションを使用するには、次の手順を実行します。
  - プランを右クリックし、コンテキスト メニューで [ノードの検索] オプションをクリックします。
  - CTRL + F キーを使用します。


**Analysis Services (AS)**

- SSMS の AS Azure モデルにメール アドレスがないユーザーに対する新しい AAD ロール メンバー選択

**Integration Services (IS)**

- SSIS の実行レポートに追加された新しい列 ([実行数])

### <a name="known-issues-in-this-release"></a>このリリースの既知の問題:

- "Active Directory - MFA を使用したユニバーサルのサポート" を使用するクエリ ウィンドウを 1 時間開いた後でクエリを実行しようとすると、次のようなエラーが発生する場合があります。

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of ConnectRetryCount to increase the number of recovery attempts.`

   クエリを再実行すると、エラーを克服して成功します。

- MFA を使用したユニバーサル認証を使用する Azure AD 認証では、次の SSMS 機能はサポートされていません。
  - **新しいテーブル/ビュー** デザイナーが古いスタイルのログイン プロンプトを表示して、Azure AD の認証で機能しません。
  - **[上位 200 行を編集]** 機能は、Azure AD 認証をサポートしません。
  - **登録済みサーバー** コンポーネントは、Azure AD 認証をサポートしません。
  - **データベース エンジン チューニング アドバイザー**は、Azure AD 認証でサポートされていません。 ユーザーに表示されるエラー メッセージがあまり役に立たないという既知の問題があります。"*Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,...*" (ファイルまたはアセンブリ 'Microsoft.IdentityModel.Clients.ActiveDirectory を読み込めませんでした...) が、正常なメッセージである "*Database Engine Tuning Advisor does not support Microsoft Azure SQL Database.(DTAClient)* (Database Engine Tuning Advisor は Microsoft Azure SQL Database をサポートしていません(DTAClient)) の代わりに表示されます。

**Analysis Services (AS)**

- SSAS のオブジェクト エクスプローラーは、AS Azure の接続プロパティに Windows 認証のユーザー名を表示しません。

### <a name="bug-fixes"></a>バグの修正

- クエリの結果を (テキストとして) 印刷しようとすると発生する問題を修正しました。  https://connect.microsoft.com/SQLServer/feedback/details/3055225/
- SQL Azure データベースでテーブルとその他のオブジェクトの削除をスクリプト化したときに、SSMS が不正にこれらを破棄する問題を修正しました。
- 次のようなエラーが表示され、SSMS が時々起動しない問題を修正しました。"1 つ以上のコンポーネントが見つかりません。 アプリケーションを再インストールしてください。"
- SSMS UI の SPID が古くなって同期されない問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/1898875
- /passive 引数が /quiet として扱われる SSMS (サイレント) セットアップでの問題を修正しました。
- SSMS が起動時に時々、"オブジェクト参照がオブジェクト インスタンスに設定されていません" というエラーをスローする問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3134698
- グラフ テーブルで [計算] を押すと、SSMS がクラッシュするデータ圧縮ウィザードの問題を修正しました。
- (低速なインターネット接続を介して) テーブルのインデックスを右クリックしたときのパフォーマンスの問題に対処しました。 https://connect.microsoft.com/SQLServer/feedback/details/3120783
- 大文字と小文字を区別する照合順序を持つサーバーで、SSMS がバックアップ ファイルを列挙できない問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3134787 および https://connect.microsoft.com/SQLServer/feedback/details/3137000
- Showplan と showplan 比較のさまざまな修正
- SSMS を実行しているコンピューターに SQL Server がインストールされていないと、[接続] ダイアログで接続に使用する [ネットワーク プロトコル] をユーザーが指定できない問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3134997
- 一部の SSMS ダイアログが "ランダム" な場所に表示されるマルチ モニター構成のサポートを強化しました。 タスク ダイアログやプロパティ シートを閉じたときにその位置を記憶できるように、[SQL Server オブジェクト エクスプローラー | コマンド] ユーザー設定の下に、新しいオプション [タスク ダイアログ] が追加されました。 https://connect.microsoft.com/SQLServer/feedback/details/889169、 https://connect.microsoft.com/SQLServer/feedback/details/1158271、 https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- SSMS が暗号化された Azure SQL DB の DB プロパティを変更できない問題を修正しました。
- [実行後に結果を破棄する] オプションを強化しました。 https://connect.microsoft.com/SQLServer/feedback/details/1196581
- ユーザーが自分が管理者ではない Azure サブスクリプションにアクセスできない問題を改善または修正しました。
- ソース データベースの選択に関係なく、OE で選択したターゲット データベースを維持するようにデータベースの復元ウィザードを改善しました。 https://connect.microsoft.com/SQLServer/feedback/details/3118581
- オブジェクト エクスプローラーが、新しく追加された "ネイティブ コンパイル ストアド プロシージャ" を正しく並べ替えない問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3133365
- "SELECT TOP n ROWS" に "TOP" 句が含まれない問題を修正しました。 Azure SQLDW の場合。 https://connect.microsoft.com/SQLServer/feedback/details/3133551 および https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI: すべてのレポートで非カスタム時間間隔が正しく動作しない問題を修正しました。
- Always Encrypted:新しい CMK ダイアログの AKV アクセス許可の状態に関するメッセージングを改善しました。名前が長い CEK を区別しやすいように CEK ドロップダウンにツールヒントが追加されました。一部の CNG キー ストア プロバイダーが Always Encrypted の [新しい列マスター キー] ダイアログに表示されない問題が修正されました
- SSMS 接続の一貫性のない "Application Name" を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3135115
- SSMS が SQL Azure に対して正しいスクリプトを生成しない (DATA_COMPRESSIONS オプションを使用したテーブルとインデックス) 問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3133148
- ユーザーが CTRL + Q のショートカット キーを使用してクイック起動できない問題を修正しました (注: クエリ エディターで [IntelliSense が有効] オプションを切り替える新しいキー バインディングは、CTRL + B と CTRL + I になりました)。 https://connect.microsoft.com/SQLServer/feedback/details/3131968
- カスタム ドメインが定義されたアカウントを持つサブスクリプションからストレージ アカウントを選択しようとすると、SSMS が例外をスローする "データベースの復元" での問題を修正しました。
- SSMS が "インデックスが配列の境界外です" エラーをスローし、ユーザーが "テーブル ビュー" を標準以外のものに変更できない "データベース ダイアグラム" での問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3133792 および https://connect.microsoft.com/SQLServer/feedback/details/3135326
- SSMS が従来のストレージ アカウントを列挙しない "URL へのバックアップ/復元" での問題を修正しました。
- データベース ロールにスキーマ バインドのセキュリティ保護可能を追加しようとすると、例外がスローされる問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3118143
- テーブル ノードの展開時に、SSMS が断続的に次のエラーを表示する問題を修正しました。"データが NULL です。 このメソッド、またはプロパティは Null 値で呼び出せません。" https://connect.microsoft.com/SQLServer/feedback/details/3136283
- DTA:特定の境界値を持つパーティション関数を評価するときに、ヒープの破損により DTAEngine.exe が終了する問題を修正しました。


**Analysis Services (AS)**

- データベースに ID とは異なる名前が含まれていると、AS データベースの復元がエラーにより失敗する問題を修正しました。
- DAX クエリ ウィンドウで [IntelliSense が有効] を切り替えるメニュー オプションが無視される問題を修正しました。
- msmdpump IIS http/https アドレスを介した SSAS への接続を妨げる問題を修正しました。
- セミコロンが含まれているパスワードを使用して AS Azure に接続できるようになりました
- [メンバーシップのスキップ] オプションを使用して AS データベースの復元コマンドのスクリプトを作成すると、SQL Server 2017 AS サーバーまたは AS Azure で使用するときに対応する新しい JSON オプションが含まれます。
- 読み込み時にデータベースの削除ダイアログにエラーを引き起こす非常にまれな問題を修正しました。
- SQL クエリと M のパーティション定義が混在する 1400 互換性レベル モデルでパーティションを表示しようとするときに発生する可能性のある問題を修正しました。

**Integration Services (IS)**
- SSISDB カタログの実行情報レポートを表示できない問題を修正しました。
- 多数のプロジェクトまたはパッケージによるパフォーマンス低下に関する SSMS の問題に対処しました。

## <a name="downloadssdtmediadownloadpng-ssms-171httpsgomicrosoftcomfwlinklinkid849819"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.1](https://go.microsoft.com/fwlink/?linkid=849819)
一般公開 | ビルド番号:14.0.17119.0

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

### <a name="enhancements"></a>機能強化

- Profiler:[ヘルプ] > [バージョン情報] でリリース バージョン番号 (例: 17.1) が表示されるようになりました
- Analysis Service のユーザーは、データ ソースのコンテキスト メニューから 1200 TM モデル以降のデータ ソースの資格情報を更新できます
- 組み込み SSIS レポートで、CTP 2.1 での SSIS スケールアウト実行からのログが表示されるようになりました
- SSIS スケールアウト管理アプリケーション
  - スケールアウト マスターに関する基本的な情報を表示します。
  - スケールアウトの配置に worker を簡単に追加します。
  - すべてのスケールアウト worker とそれらに関する基本情報を表示し、それらを簡単に有効化または無効化することもできます。

### <a name="bug-fixes"></a>バグの修正
- Always On:
  - 可用性レプリカのプロパティが WSFC AG に対して常に "自動フェールオーバー" モードと表示された問題を修正しました。
  - 可用性グループを更新すると読み取り専用ルーティング リストが上書きされた問題を修正しました
- Always Encrypted: 生成されたログ ファイルに DacFx によって生成された情報が含まれない問題を修正しました。
- プラン表示: 適応型結合ではない演算子に対して、UI に常に実際の結合の種類属性が表示されていた問題を修正しました。
- セットアップ:
  - SSMS 17.0 が Visual Studio 2013 の SSDT を壊していた問題を修正しました [Connect アイテム 3133479]
  - セットアップの最後で [再起動] をクリックしてもコンピューターが再起動しなかった問題を修正しました
- スクリプト: 削除スクリプトを作成しようとするときに SSMS が誤って Azure データベース オブジェクトを削除しないようにそのオプションを無効にすることで一時的に防止しています。  適切な修正は SSMS の今後のリリースで行われます。
- オブジェクト エクスプローラー: "AS COPY" を使って作成された Azure データベースに接続したときに "データベース" ノードが展開されなかった問題を修正しました

## <a name="downloadssdtmediadownloadpng-ssms-170httpsgomicrosoftcomfwlinklinkid847722"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.0](https://go.microsoft.com/fwlink/?LinkID=847722)
一般公開 | ビルド番号:14.0.17099.0

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40a)

### <a name="enhancements"></a>機能強化 

- アップグレード パッケージと Windows Software Update Services (WSUS) の今後の 17.X リリースには、より小さい累積的な更新パッケージが含まれます 
  - 更新プログラム パッケージは、WSUS カタログにも公開されます  
- 更新プログラム アイコンは VS シェルに表示されるアイコンと一貫性があり、16.X と 17.X のバージョンを区別する新しい SSMS およびプロファイラーのプログラム アイコンの高 DPI の解像度をサポートするように更新されました。
- SQL PowerShell モジュール
  - SQL Server PowerShell モジュールは、SSMS から削除され、PowerShell ギャラリーを介してリリースされます (モジュールのバージョン管理をサポートするには PowerShell 5.0 が必要です)
  - 一部の SMO オブジェクトの "プレゼンテーション" (書式設定) に関連するその他の改善 (たとえば、データベースでサイズと使用可能領域が、テーブルで行数と領域の使用状況が表示されるようになりました)
  - OE で PowerShell コマンド プロンプトが [PowerShell の起動] メニューから呼び出されたときのカラー化が追加されました
  - AG コマンドレットに (New-SqlAvailabilityGroup、Join-SqlAvailabilityGroup、および Set-SqlAvailabilityGroup) に -ClusterType パラメーターと -RequiredCopiesToCommit パラメーターを追加しました。
  - Add-SqlAzureAuthenticationContext コマンドレットに -ActiveDirectoryAuthority パラメーターと -AzureKeyVaultResourceId パラメーターを追加しました。
  - Revoke-SqlAvailabilityGroupCreateAnyDatabase、Grant-SqlAvailabilityGroupCreateAnyDatabase、Set-SqlAvailabilityReplicaRoleToSecondary の各コマンドレットが追加されました
  - Set-SqlAvailabilityReplica および New-SqlAvailabilityReplica コマンドレットに -SeedingMode パラメーターが追加されました
  - -ConnectionString パラメーターが Get-SqlDatabase に追加されました
- ログ配布に対する SQL Server on Linux の一般的な機能強化と修正
  - ネイティブ Linux パスの Attach、Restore、Backup データベースのサポートが追加されました
  - 監査ログ宛先フォルダーのネイティブ Linux パスのサポートが追加されました
- Analysis Services
  - DAX クエリ ウィンドウ:
    - エディターでのかっこの照合
    - DEFINE MEASURE と DEFINE VAR の構文のサポート
    - さまざまな Intellisense の機能強化
  - ユニバーサル認証
    - ユーザーはパスワードを指定しないでユーザー名を指定することができ、Azure ログイン ダイアログが接続を処理します
  - SSMS PQ 統合: 
    - 構造化されたデータ ソースのスクリプトが機能します 
    - PQ UI で構造化されたデータ ソースの表示と編集
- 新しい [一意制約の追加] テンプレート
- Showplan で、経過時間についてプロパティ ウィンドウのスレッド全体の合計ではなく、最大値が表示されます。新しい mem grant 演算子のプロパティを公開します。ライブ クエリの統計の [クエリの編集] ボタンが有効になりました。インターリーブ実行のサポート。
  - [実際の実行プランの分析] の新しいオプション
  - プラン表示の比較に対する全般的改良
  - プラン表示の比較機能に、2 つのクエリ プランの一致するノード間のカーディナリティ推定での大きな違いを見つけて、考えられる根本原因の基本分析を実行する機能が導入されました。
- 登録済みサーバー エクスプローラーから Configuration Manager を削除しました。
- Azure Blob ストレージから監査ログを読み取り可能
- Always Encrypted にパラメーター化機能が追加されました。詳細については、[このページ](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/)を参照してください。 
- Azure SQL DB への AAD ユニバーサル認証接続でカスタム テナント ID がサポートされます 
- Azure SQL Database のスクリプト生成で、テキスト、ルール、およびデータベースが完全にスクリプト化されるようになりました。
- スプラッシュ スクリーンでの SSMS と Profiler のブランド化が修正されました。
- SSMS からユーティリティ コントロール ポイントの UI が削除されました。
- SSMS は "PremiumRS" エディションの SQL Azure データベースを作成できるようになりました
- Always On 可用性グループ
  - 新しいクラスターの種類の EXTERNAL と NONE のサポートが追加されます。Linux での SQL Server 2000 のサポートが追加されます。初期データ同期のためのオプションとして、自動シード処理が追加されます。エンドポイント URL の処理、DB の更新や UI のレイアウトなど、いくつかの欠陥を修正しました。Azure レプリカ関連の機能を削除しました
  - いくつかの可用性グループ キーワードについて IntelliSense を改善しました
- 利用状況モニター
  - SSMS 出力ウィンドウに新しい [利用状況モニター] ウィンドウを追加しました
  - ポップアップ メッセージではなく出力ウィンドウに情報を記録するように、接続エラー/タイムアウト メッセージを変更しました
  - [概要] セクションで空グラフ (5 番目のグラフ) を削除しました
  - 利用状況モニターのデータ収集が一時停止した場合の [(一時停止)] を [概要] タイトルに追加しました
  - SQL Server のグラフの強化。グラフ ノードとエッジ テーブルの新しいアイコン。グラフ ノードとエッジ テーブルが [グラフ テーブル] フォルダーに表示されます。グラフ ノードとエッジ テーブルを作成するためのテンプレートを使用できます。
- プレゼンテーション モード: 3 つの新しいタスクがクイック起動 (Ctrl + Q) で使用できるようになりました。PresentOn: プレゼンテーション モードを有効にします。PresentEdit: プレゼンテーション モードのプレゼンテーションのフォント サイズを編集します。  クエリ エディター用の "テキスト エディター フォント"。  その他のコンポーネント用の "環境フォント"。
RestoreDefaultFonts: 既定の設定に戻ります。
*注: 現時点では、PresentOff コマンドは存在しません。プレゼンテーション モードをオフにするには、RestoreDefaultFonts を使用します。*

### <a name="bug-fixes"></a>バグの修正

- surface book タッチパッドでプラン表示をスクロールしたときに SSMS がクラッシュする問題を修正しました
- 復元中またはオフライン中のデータベースのプロパティを取得するときに SSMS が長時間ハングする問題を修正しました 
- RC ビルドで "ヘルプ ビューアー" が開かない問題を修正しました
- "メンテナンス プラン タスク ツールボックス" アイテムが SSMS にない問題を修正しました。
- データベースの名前に中かっこが含まれている場合にデータベースを圧縮できない SSMS の問題を修正しました。 [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3122618)を参照)。
- SSMS が Azure データベースの削除をスクリプト化しようとして実際にはデータベース自体を削除していた問題を修正しました。 [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3131458/)を参照)。
- ユーザー定義テーブル型で既定値がスクリプト化されない問題を修正しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3119027)を参照)。
- インデックスのコンテキスト メニューに関するパフォーマンスの改善を再度実行しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3120783)を参照)。
- 実行プランで欠落インデックスの上にマウスを置いたときに過剰なちらつきを発生させる問題を修正しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3118510)を参照)。
- スクリプト作成時に SSMS の DB オフラインがオンラインになる問題を修正しました ([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3118550)を参照)。
- SSMS のローカライズされた (英語以外の) バージョンで、さまざまな UI の修正を実行しました。
- SQL 2016 SP1 Standard Edition をターゲットとした場合に [Always Encrypted キー] ノードが欠落する問題を修正しました。
- Always Encrypted: SQL 2016 RTM Standard Edition または任意の SQL 2014 (以下の) サーバーをターゲットにするときに [Always Encrypted] メニューが正しく有効になりませんでした。CREATE または ALTER 構文を使用すると、IntelliSense でエラーが報告される問題を修正しました。CMK/CEK にエスケープする必要がある (角かっこで囲まれた) 文字が含まれていた場合、暗号化が失敗する問題を修正しました。SSMS でメモリ不足例外が発生すると、代わりにネイティブ (64 ビット) の PowerShell の使用を提案するエラーがユーザーに表示されます。
ユーザーが従来の Azure サブスクリプションではなく Resource Group Manager サブスクリプションを使用した場合に AE ウィザードが失敗する問題を修正しました。ユーザーがいずれのサブスクリプションにもアクセス許可がないか Azure Key Vault を持っていない場合に、AE ウィザードに適切でないエラーが表示される問題を修正しました。
複数の AAD があるときに Azure Key Vault のサインイン ページに Azure サブスクリプションが表示されないという AE ウィザードの問題を修正しました。Azure Key Vault のサインイン ページに、ユーザーが閲覧者アクセス許可を持っている Azure サブスクリプションが表示されないという AE ウィザードの問題を修正しました。
  - リソース ファイルを正しく読み込めず、不正確なエラー メッセージを表示していた問題を修正しました
- SSMS の [セットアップ] ページ上のハイパーリンクのコントラストを改善しました。
- SQL Server Express (2016 SP1) に接続したときに PolyBase ノードが表示されない問題を修正しました
- SSMS が Azure DB の互換性レベルを v140 に変更できない問題を修正しました
- Azure データベースの一覧を展開するときのオブジェクト エクスプローラーのパフォーマンスを強化しました ([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3100675)を参照)。
- リレーショナル サーバー以外の種類のサーバー (AS\RS\IS) で [SQL Server ログの表示] コンテキスト メニュー項目が間違って表示される問題を修正しました。 
- SQL 認証を使用する Analysis Services のパーティション クエリの構文チェックで、ログイン失敗メッセージが表示される問題を修正しました。
- SSMS で、プレビュー 1400 コンパクト レベルの AS 表形式モデルの名前を変更するとエラーが発生する問題を修正しました。
- まれな状況で、AS サーバー上で無効な操作を試行した後で発生する可能性がある "モデルの操作に失敗する" 問題を修正しました。モデルの保存に失敗した後、ローカルの変更は元に戻ります
- Analysis Services 同期データベースのポップアップ ダイアログの文字の間違いを修正しました。
- コンテナーのバックアップ/復元ダイアログが、複数のモニター セットアップで画面の表示領域を超えて表示される。 
- ターゲット オブジェクトの名前に `]` が含まれている場合、SecurityPolicy を作成できない。
- SSMS 2016 の [最近使用した項目を開く] メニューに、最近保存したファイルが表示されない ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)を参照)。
- VS Shell の更新時のユーザー設定のリセットが削除されました。
- ユーザーが SQL Server 2017 のデータベースの互換性レベルを変更できないという問題を修正しました。
- AAD ユニバーサル認証を使用するクエリ ウィンドウで、1 時間後にクエリを更新できなくなる。
- SSMS からユーティリティ コントロール ポイントの UI が削除されました。
- トークンの初期の有効期限が切れると、AD ユニバーサル認証接続でデータを照会できない。
- Azure SQL DB 間のルールをスクリプト化できない。
- SQL PowerShell が以前の SQL インスタンス (2014 以前) に接続できないという問題が修正されました。 [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)を参照)。
- 登録済みサーバーのインポートに失敗すると SSMS がクラッシュする原因となる問題が修正されました。
- ユーザーにデータベースに対する特定のアクセス許可がある場合に SSMS がクラッシュする原因となる問題が修正されました。
- SSMS - ビューの確認時にデザイン画面にテーブルが表示されなくなる ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views)を参照)。 
- テーブルのスクロール バーでテーブルの内容をスクロールできない。上下の方向キーでのみスクロールできる。 バグがあるスクロール バーを使用してスクロールを試した後で、テーブルの内容をスクロールできる場合もある ( [Connect アイテム](
https://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view)を参照)。 
- ルート ノードを更新した後、登録済みサーバーにアイコンが表示されない。
- Azure v12 サーバーで [データベースの作成] のスクリプト ボタンを使用してスクリプトを実行すると、"スクリプトを作成するアクションはありません" というメッセージが表示される。
- SSMS の [サーバーに接続] ダイアログで、新しい接続ごとの [追加のプロパティ] タブがクリアされない。
- タスクの生成スクリプトで、Azure SQL DB のデータベースの生成スクリプトが生成されない。
- ビュー デザイナーのスクロール バーが無効になっているように表示される。
- Always Encrypted AVK キーのパスにバージョン ID が含まれていない。
- クエリ ウィンドウ内のエンジン エディション クエリの数が削減されました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3113387)を参照)。
- 暗号化が正しく処理されていない状態でモジュールを更新すると、Always Encrypted でエラーが発生する。
- OLTP と OLAP の既定の接続タイムアウト値が 15 秒から 30 秒に変更され、無視された接続エラーのクラスが修正されました。 
- カスタム レポートの起動時の SSMS のクラッシュが修正されました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3118856)を参照)。
- Azure SQL データベースに対する [スクリプトの生成...] が失敗する問題を修正しました。
- [スクリプト化] と [スクリプトの生成] ウィザードが修正され、ストアド プロシージャなどのオブジェクトのスクリプト化の際に余分な改行が追加されないようになります ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3115850)を参照)。
- SQLAS PowerShell プロバイダー:Dimension および MeasureGroup フォルダーに LastProcessed プロパティが追加されます ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3111879)を参照)。
- ライブ クエリ統計: バッチの最初のクエリしか表示されないという問題が修正されました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3114221)を参照)。  
- プラン表示: プロパティ ウィンドウにスレッド全体の合計ではなく、最大値が表示される。
- クエリ ストア: 豊富な実行バリエーションの新しいレポートがクエリに追加される。
- オブジェクト エクスプローラーのパフォーマンスの問題:([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3114074)を参照)。テーブルのコンテキスト メニューがすぐにハングする。テーブルのインデックスを右クリックすると、SSMS の動作が遅くなる (リモート (インターネット) 接続経由の場合)。 サーバーでのテーブルの並べ替えクエリの発行を避ける。
- SSMS から (Azure VM にデータベースを展開するための) Azure 展開ウィザードが削除されました。
- SSMS の実行プランに不足しているインデックスが表示されないという問題が修正されました ([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3114194)を参照)。
- SSMS での一般的なシャットダウン時のクラッシュの問題が修正されました。
- オブジェクト エクスプローラーで、PolyBase|スケールアウト グループ ノードのコンテキスト メニューを表示したときにエラーが発生する問題が修正されました ([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3115128)を参照)
- データベースに対するアクセス許可を表示しようとすると SSMS がクラッシュする場合があるという問題が修正されました。
- クエリ ストア: クエリ ストア レポートの結果グリッドのコンテキスト メニュー項目が全体的に改善されました。
- 関連付けられていないオブジェクトで既存のテーブルに対して Always Encrypted を構成すると、エラーが発生して実行できない ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3103181)を参照)。
- 複数のスキーマを持つ既存のデータベースに対して Always Encrypted を構成できない ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3109591)を参照)。
- データベースにシステム ビューを参照するビューが含まれているため、Always Encrypted の暗号化された列ウィザードでエラーが発生する ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3111925)を参照)。
- Always Encrypted を使用して暗号化する場合、暗号化が正しく処理されていない状態でモジュールを更新するとエラーが発生する。
- [新規サーバーの登録] ダイアログで UI が切り捨てられる問題が修正されました。
- 引用符で囲まれた文字列定数値を含む式が DMF 条件 UI で正しく更新されない問題が修正されます。
- カスタム レポートの実行時に SSMS がクラッシュする原因と思われる問題が修正されました。
- [Execution in Scale Out...]\(スケールアウトで実行...\) メニュー項目がフォルダー ノードに追加されます
- Azure SQL DB ファイアウォール ホワイト リスト IP アドレス機能の問題を修正しました
- AS 多次元パーティションのソースの編集時にオブジェクト参照が例外を設定しない原因であった SSMS の問題を修正しました
- 多次元 AS サーバーから顧客アセンブリを削除するときにオブジェクト参照が例外を設定しない原因であった SSMS の問題を修正しました
- AS テーブル 1400 db の名前変更が失敗した問題を修正しました
- 接続プロパティ ダイアログからの 1400 互換性レベル AS テーブル データソースのスクリプト化に関する問題を修正しました
- 1400 互換性レベル モデル内のテーブルが少なくとも 1 つのパーティションを持つという前提を削除しました
- Ctrl + R キーで SSMS DAX クエリ エディターの結果ウィンドウが切り替わるようになりました


## <a name="downloadssdtmediadownloadpng-ssms-1653httpsgomicrosoftcomfwlinklinkid840946"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 16.5.3](https://go.microsoft.com/fwlink/?LinkID=840946)
一般公開 | ビルド番号:13.0.16106.4

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)

このリリースでは次の問題が修正されました。

* SSMS 16.5.2 で、テーブルに複数のスパース列がある場合に 'Table' ノードが拡張される原因となっていた問題が修正されました。

* ユーザーは、SSIS カタログに、Microsoft Dynamics AX/CRM Online のリソースに接続される OData 接続マネージャーを含む SSIS パッケージを展開できます。 詳細については、「[OData 接続マネージャー](../integration-services/connection-manager/odata-connection-manager.md)」を参照してください。

* 関連付けられていないオブジェクトで既存のテーブルに対して Always Encrypted を構成すると、エラーが発生して実行できない ( [Connect ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects) を参照)。

* 複数のスキーマを持つ既存のデータベースに対して Always Encrypted を構成できない ( [Connect ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work) を参照)。

* データベースにシステム ビューを参照するビューが含まれているため、Always Encrypted の暗号化された列ウィザードでエラーが発生する ( [Connect ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors) を参照)。

* Always Encrypted を使用して暗号化する場合、暗号化が正しく処理されていない状態でモジュールを更新するとエラーが発生する。

* *[最近使用した項目を開く]* メニューに、最近保存したファイルが表示されない ( [Connect ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files) を参照)。

* テーブルのインデックスを右クリックすると SSMS の動作が遅くなる (リモート (インターネット) 接続経由の場合)。 [Connect ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection) を参照)。
 
* SQL デザイナーのスクロール バーの問題が修正されました ( [Connect ID 3114856](https://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016) を参照)。

* テーブルのコンテキスト メニューがすぐにハングする。 
 
* SSMS で利用状況モニターの例外がスローされ、クラッシュする場合がある ( [Connect ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/) を参照)。

* ".NET ランタイムの内部エラーにより、処理が中止されました。IP 71AF8579 (71AE0000)、終了コード 80131506" という内容のエラーで SSMS 2016 がクラッシュする。


## <a name="uninstall-and-reinstall-ssms-17x"></a>SSMS 17.x をアンインストールおよび再インストールする

SSMS のインストールで問題があり、標準のアンインストールと再インストールでは解決されない場合、最初に Visual Studio 2015 IsoShell の[修復](https://support.microsoft.com/help/4028054/windows-10-repair-or-remove-programs)をお試しください。 Visual Studio 2015 IsoShell の修復で問題が解決しない場合、多数のランダムな問題は次の手順で修正されることが確認されています。

1.  アプリケーションをアンインストールする場合と同じ方法で、SSMS をアンインストールします (Windows のバージョンに応じて *[アプリと機能]*、*[プログラムと機能]* などを使用する)。

2.  **管理者特権でのコマンド プロンプトから** Visual Studio 2015 IsoShell をアンインストールします。
   
    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```

    ```vs_isoshell.exe /Uninstall /Force /PromptRestart```

3.  アプリケーションをアンインストールする場合と同じ方法で、Microsoft Visual C++ 2015 再頒布可能パッケージをアンインストールします。 コンピューター上に x86 と x64 がある場合は、両方ともアンインストールします。

4.  **管理者特権でのコマンド プロンプトから** Visual Studio 2015 IsoShell を再インストールします。  

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```  
 
    ```vs_isoshell.exe /PromptRestart```

5.  SSMS を再インストールします。

6.  最新バージョンでない場合は、[最新バージョンの Visual C++ 2015 再頒布可能パッケージ](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)にアップグレードします。


## <a name="additional-downloads"></a>追加のダウンロード  
すべての SQL Server Management Studio ダウンロードの一覧については、「[Microsoft ダウンロード センター](https://www.microsoft.com/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending)」を検索してください。  
  
SQL Server Management Studio の最新リリースについては、「[SQL Server Management Studio &#40;SSMS&#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)」を参照してください。  
