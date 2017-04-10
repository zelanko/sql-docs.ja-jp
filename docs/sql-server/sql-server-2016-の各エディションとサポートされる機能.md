---
title: "SQL Server 2016 の各エディションとサポートされる機能 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "sql エディション"
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
caps.latest.revision: 175
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
---
# SQL Server 2016 の各エディションとサポートされる機能
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のさまざまなエディションでサポートされる機能の詳細について説明します。  
  
 180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
  
 最新のリリース ノートと新機能については、以下の情報を参照してください。
- [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
- [SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)

    
 **SQL Server 2016 をお試しください。**    
    
 > [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Evaluation Center から SQL Server 2016 をダウンロードする](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Azure Virtual Machine のアイコン](../analysis-services/media/azure-virtual-machine-small.png) **[SQL Server 2016 がインストール済みの Virtual Machine をすぐにご利用いただけます](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    
    
  
 Evaluation Edition および Developer Edition でサポートされている機能については、SQL Server Enterprise Edition をご覧ください。  
  
##  <a name="a-namecross-boxscalelimitsa-scale-limits"></a><a name="Cross-BoxScaleLimits"></a> スケールの制限  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限| 
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] または [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとのバッファー プールの最大メモリ|オペレーティング システムの最大容量|128 GB|64 GB|1410 MB|1410 MB|
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとの列ストア セグメント キャッシュの最大メモリ|メモリ制限なし| 32 GB<sup>2</sup>| 16 GB<sup>2</sup>| 352 MB<sup>2</sup>| 352 MB<sup>2</sup>|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のデータベースごとの最大メモリ最適化データ サイズ|メモリ制限なし| 32 GB<sup>2</sup>| 16 GB<sup>2</sup>| 352 MB<sup>2</sup>| 352 MB<sup>2</sup>|  
|利用可能な最大メモリ サイズ ([!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスごと)|オペレーティング システムの最大容量|テーブル: 16 GB<br /><br /> MOLAP: 64 GB|なし|なし|なし|  
|利用可能な最大メモリ サイズ ([!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のインスタンスごと)|オペレーティング システムの最大容量|64 GB|64 GB|4 GB|なし|
|リレーショナル データベースの最大サイズ|524 PB|524 PB|524 PB|10 GB|10 GB|  
  
 1. Enterprise Edition with Server + Client Access License (CAL) に基づくライセンス (新しい使用許諾契約では利用できません) は、SQL Server インスタンスあたり最大 20 コアに制限されています。 コアベースのサーバー ライセンス モデルでは、制限はありません。 詳細については、「 [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)」を参照してください。  
  
<sup>2</sup> [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 に適用されます。 

##  <a name="a-namerdbmshaa-rdbms-high-availability"></a><a name="RDBMSHA"></a> RDBMS の高可用性  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Server Core サポート <sup>1</sup>|可|可|可|可|可|  
|ログ配布|可|可|可|不可|不可|  
|データベース ミラーリング|可|可<br /><br /> FULL SAFETY のみ|ミラーリング監視のみ|ミラーリング監視のみ|ミラーリング監視のみ| 
|バックアップ圧縮|可|可|不可|不可|不可| 
|データベース スナップショット|可|可 <sup>3</sup>|可 <sup>3</sup>|可 <sup>3</sup>|可 <sup>3</sup>|
|Always On フェールオーバー クラスター インスタンス|可<br /><br /> ノードの数はオペレーティング システムの最大容量|可<br /><br /> 2 つのノードのサポート|不可|不可|不可|  
|Always On 可用性グループ|可<br /><br /> 2 個の同期セカンダリ レプリカを含む最大 8 個のセカンダリ レプリカ|不可|不可|不可|不可|
|基本的な可用性グループ <sup>2</sup>|不可|可<br /><br /> 2 つのノードのサポート|不可|不可|不可|
|接続ディレクター|可|不可|不可|不可|不可|
|オンライン ページおよびファイルの復元|可|不可|不可|不可|不可|
|オンラインのインデックス構築|可|不可|不可|不可|不可|
|オンラインのスキーマ変更|可|不可|不可|不可|不可|
|高速復旧|可|不可|不可|不可|不可|
|ミラー化バックアップ|可|不可|不可|不可|不可|
|ホット アド メモリと CPU|可|不可|不可|不可|不可|
|データベース復旧アドバイザー|可|可|可|可|可|
|暗号化されたバックアップ|可|可|不可|不可|不可|
|Windows Azure へのハイブリッド バックアップ (URL へのバックアップ)|可|可|不可|不可|不可|  
  
 <sup>1</sup> Server Core への SQL Server 2016 のインストールの詳細については、「[Server Core への SQL Server 2016 のインストール](../database-engine/install-windows/install-sql-server-2016-on-server-core.md)」を参照してください。 

<sup>2</sup> 基本的な可用性グループの詳細については、「[基本的な可用性グループ](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md)」を参照してください。  

<sup>3</sup> [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1 に適用されます。
  
##  <a name="a-namerdbmsspa-rdbms-scalability-and-performance"></a><a name="RDBMSSP"></a> RDBMS のスケーラビリティとパフォーマンス  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|列ストア <sup>1</sup>|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|  
|インメモリ OLTP <sup>1</sup>|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>、<sup>3</sup>|可 <sup>2</sup>|
|Stretch Database|可|可|可|可|可|
|恒久的なメイン メモリ|可|可|可|可|可|
|複数インスタンスのサポート|50|50|50|50|50|
|テーブルとインデックスのパーティション分割|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|  
|データ圧縮|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|
|[リソース ガバナー]|可|不可|不可|不可|不可|  
|パーティション テーブルの並列処理|可|不可|不可|不可|不可|
|複数の Filestream コンテナー|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|
|NUMA 対応のラージ ページ メモリとバッファー配列の割り当て|可|不可|不可|不可|不可|
|バッファー プール拡張|可|可|不可|不可|不可|
|IO リソース管理|可|不可|不可|不可|不可|  
|遅延持続性|可|可|可|可|可|

<sup>1</sup> インメモリ OLTP データ サイズおよび列ストア セグメント キャッシュは、「スケールの制限」セクションでエディションごとに指定されているメモリ量に制限されます。 並列処理には最大限度があります。 インデックス構築のための並列処理の度合い (DOP) は、Standard Edition では 2 DOP に、Web および Express Edition では 1 DOP に制限されます。 これは、ディスク ベース テーブルとメモリ最適化テーブルで作成された列ストア インデックスに当てはまります。

<sup>2</sup> [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 に適用されます。 

<sup>3</sup> LocalDB のインストール オプションには、この機能は含まれていません。
##  <a name="a-namerdbmssa-rdbms-security"></a><a name="RDBMSS"></a> RDBMS のセキュリティ  
  
|機能|Enterprise|Standard|Web|Express|Express with Advanced Services|  
|-------------|----------------|--------------|---------|-------------|------------------------------------| 
|行レベルのセキュリティ|可|可|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>|  
|Always Encrypted|可|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>| 
|動的なデータ マスキング|可|可|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>|   
|基本的な監査|可|可|可|可|可| 
|詳細な監査|可|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>| 
|透過的なデータベースの暗号化|可|不可|不可|不可|不可|   
|拡張キー管理|可|不可|不可|不可|不可| 
|ユーザー定義ロール|可|可|可|可|可| 
|包含データベース|可|可|可|可|可| 
|バックアップの暗号化|可|可|不可|不可|不可|  

<sup>1</sup> [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1 に適用されます。  
##  <a name="a-namereplicationa-replication"></a><a name="Replication"></a> レプリケーション  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|異種サブスクライバー|可|可|不可|不可|不可|  
|マージ レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|Oracle パブリッシュ|可|不可|不可|不可|不可| 
|ピア ツー ピア トランザクション レプリケーション|可|不可|不可|不可|不可|   
|スナップショット レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|SQL Server の変更の追跡|可|可|可|可|可| 
|トランザクション レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|Azure へのトランザクション レプリケーション|可|可|可|不可|不可|   
|トランザクション レプリケーションの更新可能サブスクリプション|可|不可|不可|不可|不可|  
  
##  <a name="a-namessmsa-management-tools"></a><a name="SSMS"></a> 管理ツール  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SQL 管理オブジェクト (SMO)|可|可|可|可|可|  
|SQL 構成マネージャー|可|可|可|可|可|   
|SQL CMD (コマンド プロンプト ツール)|可|可|可|可|可|      
|分散再生 - 管理ツール|可|可|可|可|不可|  
|分散再生 - クライアント|可|可|可|不可|不可|  
|分散再生 - コントローラー|可 (最大 16 クライアント)|可 (1 クライアント)|可 (1 クライアント)|不可|不可|   
|SQL Profiler|可|可|不可 <sup>1</sup>|不可 <sup>1</sup>|不可 <sup>1</sup>|  
|SQL Server エージェント|可|可|可|不可|不可| 
|Microsoft System Center Operations Manager 管理パック|可|可|可|不可|不可|  
|データベース チューニング アドバイザー (DTA)|可|可 <sup>2</sup>|可 <sup>2</sup>|不可|不可|      
  
 <sup>1</sup> SQL Server Web、SQL Server Express、SQL Server Express with Tools、および SQL Server Express with Advanced Services は、SQL Server Standard および SQL Server Enterprise の各エディションを使用してプロファイルできます。  
  
 <sup>2</sup> チューニングは Standard Edition 機能でのみ有効です。  
  
##  <a name="a-namerdbmsma-rdbms-manageability"></a><a name="RDBMSM"></a> RDBMS の管理の容易性  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|ユーザー インスタンス|不可|不可|不可|可|可| 
|LocalDB|不可|不可|不可|可|不可| 
|専用管理者接続|可|可|可|可 (トレース フラグを使用)|可 (トレース フラグを使用)|   
|PowerShell スクリプティングのサポート|可|可|可|可|可| 
|SysPrep のサポート <sup>1</sup>|可|可|可|可|可| 
|データ層アプリケーション コンポーネントの操作のサポート - 抽出、配置、アップグレード、削除|可|可|可|可|可| 
|ポリシー オートメーション (変更時とスケジュールに基づいて確認)|可|可|可|不可|不可|   
|パフォーマンス データ コレクター|可|可|可|不可|不可| 
|複数インスタンス管理でマネージ インスタンスとして登録できる|可|可|可|不可|不可|   
|標準的なパフォーマンス レポート|可|可|可|不可|不可| 
|プラン ガイドおよびプラン ガイドの固定計画|可|可|可|不可|不可|   
|NOEXPAND ヒントを使用したインデックス付きビューの直接クエリ|可|可|可|可|可| 
|インデックス付きビューの自動メンテナンス|可|可|可|不可|不可| 
|分散パーティション ビュー|可|不可|不可|不可|不可| 
|並列インデックス操作|可|不可|不可|不可|不可|  
|クエリ オプティマイザーによる自動的なインデックス付きのビュー使用|可|不可|不可|不可|不可| 
|並列整合性チェック|可|不可|不可|不可|不可| 
|SQL Server ユーティリティ コントロール ポイント|可|不可|不可|不可|不可|    
|バッファー プール拡張|可|可|不可|不可|不可| 
  
 <sup>1</sup> 詳細については、「[SysPrep を使用した SQL Server のインストールに関する注意点](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)」を参照してください。  
 
<sup>2</sup> [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1 に適用されます。 
  
##  <a name="a-namedevtoolsa-development-tools"></a><a name="DevTools"></a> 開発ツール  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Microsoft Visual Studio の統合|可|可|可|可|可| 
|Intellisense (Transact-SQL および MDX)|可|可|可|可|可| 
|SQL Server Data Tools (SSDT)|可|可|可|可|不可|    
|MDX 編集、デバッグ、およびデザイン ツール|可|可|不可|不可|不可|   
  
##  <a name="a-nameprogrammabilitya-programmability"></a><a name="Programmability"></a> プログラミング  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|基本的な R 統合|可|可|可|可|不可|   
|高度な R 統合|可|不可|不可|不可|不可| 
|R Server (Standalone)|可|不可|不可|不可|不可|   
|Polybase コンピューティング ノード|可|可 <sup>1</sup>|可 <sup>1</sup>、<sup>2</sup>|可 <sup>1</sup>、<sup>2</sup>|可 <sup>1</sup>、<sup>2</sup>| 
|Polybase ヘッド ノード|可|不可|不可|不可|不可| 
|JSON|可|可|可|可|可|   
|クエリ ストア|可|可|可|可|可|   
|テンポラル|可|可|可|可|可|   
|共通言語ランタイム (CLR) 統合|可|可|可|可|可|   
|ネイティブ XML サポート|可|可|可|可|可| 
|XML インデックスの作成|可|可|可|可|可| 
|MERGE と UPSERT の機能|可|可|可|可|可|   
|FILESTREAM のサポート|可|可|可|可|可| 
|FileTable|可|可|可|可|可| 
|日付および時刻データ型|可|可|可|可|可|  
|国際化サポート|可|可|可|可|可| 
|フルテキストおよびセマンティック検索|可|可|可|可|不可| 
|クエリ内の言語指定|可|可|可|可|不可|   
|Service Broker (メッセージング)|可|可|不可 (クライアントのみ)|不可 (クライアントのみ)|不可 (クライアントのみ)|   
|Transact-SQL エンドポイント|可|可|可|不可|不可| 

<sup>1</sup> 複数のコンピューティング ノードでのスケール アウトにはヘッド ノードが必要です。

<sup>2</sup> [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1 に適用されます。
  
## <a name="a-nameisa-integration-services"></a><a name="IS"></a> Integration Services

[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の各エディションがサポートする Integration Services (SSIS) の機能については、「[SQL Server 2016 の各エディションがサポートする Integration Services の機能](Integration%20Services%20Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)」をご覧ください。

##  <a name="a-namemdsa-master-data-services"></a><a name="MDS"></a> マスター データ サービス  
 [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] の各エディションがサポートする [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] と Data Quality Services の機能については、「[Master Data Services and Data Quality Services Features Supported by the Editions of SQL Server 2016](../master-data-services/master data services and data quality services features support.md)」(SQL Server 2016 の各エディションによってサポートされる Master Data Services と Data Quality Services の機能) をご覧ください。 

  
##  <a name="a-namedwa-data-warehouse"></a><a name="DW"></a> データ ウェアハウス  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|データベースを使用しないキューブ作成|可|可|不可|不可|不可 |   
|自動生成ステージングとデータ ウェアハウス スキーマ|可|可|不可|不可|不可| 
|変更データ キャプチャ|可|可 <sup>1</sup>|可 <sup>1</sup>|不可|不可| 
|スター結合クエリ最適化|可|不可|不可|不可|不可| 
|スケーラブルな読み取り専用の Analysis Services 構成|可|不可|不可|不可|不可| 
|パーティション テーブルとパーティション インデックスに対する並列クエリ処理|可|不可|不可|不可|不可|   
|グローバル バッチ集計|可|不可|不可|不可|不可| 

<sup>1</sup> [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] SP1 に適用されます。  
##  <a name="a-namessasa-analysis-services"></a><a name="SSAS"></a> Analysis Services  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] の各エディションによってサポートされる Analysis Services の機能については、「[Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。 
  
##  <a name="a-namebimda-bi-semantic-model-multi-dimensional"></a><a name="BIMD"></a> BI セマンティック モデル (多次元)  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] の各エディションによってサポートされる Analysis Services の機能については、「[Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。
   
##  <a name="a-namebita-bi-semantic-model-tabular"></a><a name="BIT"></a> BI セマンティック モデル (テーブル)  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] の各エディションによってサポートされる Analysis Services の機能については、「[Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。
  
##  <a name="a-nameppspa-power-pivot-for-sharepoint"></a><a name="PPSP"></a> Power Pivot for SharePoint  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] の各エディションによってサポートされる Power Pivot for SharePoint の機能については、「[Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。
  
##  <a name="a-namedma-data-mining"></a><a name="DM"></a> データ マイニング  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] の各エディションによってサポートされるデータ マイニングの機能については、「[Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。
  
##  <a name="a-namessrsa-reporting-services"></a><a name="SSRS"></a> Reporting Services  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] の各エディションによってサポートされる Reporting Services の機能については、「[SQL Server 2016 の各エディションがサポートする Reporting Services の機能](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)」をご覧ください。

##  <a name="a-namebica-business-intelligence-clients"></a><a name="BIC"></a> Business Intelligence クライアント  

[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] の各エディションによってサポートされる Business Intelligence クライアントの機能については、「[Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) または「[SQL Server 2016 の各エディションがサポートする Reporting Services の機能](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)」をご覧ください。
  
##  <a name="a-nameslsa-spatial-and-location-services"></a><a name="SLS"></a> 空間およびロケーション サービス  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|空間インデックス|可|可|可|可|可|   
|平面データ型と測地データ型|可|可|可|可|可| 
|高度な空間的なライブラリ|可|可|可|可|可|   
|業界標準の空間データ形式のインポート/エクスポート|可|可|可|可|可|   
  
##  <a name="a-nameadsa-additional-database-services"></a><a name="ADS"></a> その他のデータベース サービス  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------| 
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|可|可|可|可|可|   
|データベース メール|可|可|可|不可|不可| 
  
##  <a name="a-nameothera-other-components"></a><a name="Other"></a> その他のコンポーネント  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|不可|不可| 
|StreamInsight HA|StreamInsight Premium Edition|不可|不可|不可|不可|   
  
> [![SSMS をダウンロードする](../analysis-services/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[最新バージョンの SQL Server Management Studio をダウンロードする](https://msdn.microsoft.com/library/mt238290.aspx)**    
  
## <a name="see-also"></a>参照  
 [SQL Server 2016 の製品仕様](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)   
 [SQL Server 2016 のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md)  
  
  