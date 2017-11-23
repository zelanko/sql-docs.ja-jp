---
title: "エディションとサポートされる機能の SQL Server 2017 ~ Linux |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.reviewer: 
ms.suite: sql
ms.technology:
- sql-linux
- server-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- default components
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: 
caps.latest.revision: "121"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 58503277d586394e329c6232ab097a2d9d9d69cd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="editions-and-supported-features-of-sql-server-2017-on-linux"></a>エディションと SQL Server 2017 on Linux のサポートされる機能

この記事では、Linux 上の SQL Server 2017 の各種エディションでサポートされる機能の詳細を説明します。 エディションと Windows 上の SQL Server のサポートされる機能は、次を参照してください。 [SQL Server 2017 - Windows](../sql-server/editions-and-components-of-sql-server-2017.md)です。  
  
インストールの前提条件は、アプリケーションのニーズによって異なります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にはさまざまなエディションがあり、組織や個人の独自のパフォーマンス、ランタイム、および価格に関する要件に対応できます。 インストールする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントは、ユーザーの特定の要件によっても異なります。 この後のセクションでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の最適なエディションおよびコンポーネントを選択する方法について説明します。  

最新のリリース ノートと新機能については、以下の情報を参照してください。
- [Linux 上の SQL Server のリリース ノート](sql-server-linux-release-notes.md)
- [SQL Server on Linux の新機能](sql-server-linux-whats-new.md)

Linux で使用できない SQL Server 機能の一覧は、次を参照してください。[機能とサービスがサポートされていない](sql-server-linux-release-notes.md#Unsupported)です。

### <a name="try-sql-server"></a>SQL Server をお試しください    
    
[SQL Server 2017 をダウンロードします。](http://www.microsoft.com/sql-server/sql-server-2017)

## <a name="includessnoversionincludesssnoversion-mdmd-editions"></a>[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] のエディション  
 次の表で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のエディションについて説明します。 
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|定義|  
|---------------------------------------|----------------|  
|Enterprise|プレミアム製品で[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)]Enterprise edition がミッション クリティカルなワークロードの高度なサービス レベルを有効にすると非常に高速パフォーマンスを包括的なハイエンド データ センター機能を提供します。|  
|Standard|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)]Standard edition、部門や小規模組織がアプリケーションを実行するための基本的なデータ管理を提供し、オンプレミスとクラウドの一般的な開発ツールをサポートしています: 最小限の IT リソースで効果的なデータベース管理を有効にします。|  
|Web|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Web Edition は、大小さまざまな規模の Web 資産に対応できるスケーラビリティ、経済性、および管理性を備えた、Web ホスティング企業および Web VAP 向けの総保有コストの低いオプションです。|  
|開発者|開発者は、[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Developer Edition を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上で動作するあらゆる種類のアプリケーションを開発できます。 このエディションには Enterprise Edition の機能がすべて含まれていますが、実稼動サーバーとして使用するのではなく、開発およびテスト システムとしての利用に対してライセンスが供与されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Developer は、アプリケーションを作成し、テストするユーザーに適しています。|  
|Express Edition|Express Edition はエントリレベルの無料のデータベースで、学習や、デスクトップおよび小規模サーバー データ ドリブン アプリケーションの構築などに適しています。 このエディションは、独立系ソフトウェア ベンダー、開発者、クライアント アプリケーションを趣味で開発する開発者などに最適です。 さらに高度なデータベース機能が必要な場合には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の他の上位バージョンにシームレスにアップグレードできます。|  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-clientserver-applications"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] とクライアント/サーバー アプリケーションの使用  

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクライアント コンポーネントだけを、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに直接接続するクライアント/サーバー アプリケーションを実行するコンピューターにインストールできます。 クライアント コンポーネントをインストールすることは、データベース サーバー上にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを管理する場合、または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] アプリケーションを開発しようとしている場合にも適切なオプションです。  
  
## <a name="includessnoversionincludesssnoversion-mdmd-components"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]コンポーネント  

Linux 上の SQL Server 2017 には、SQL Server データベース エンジンがサポートされています。 次の表では、データベース エンジンの機能について説明します。   
  
|サーバー コンポーネント|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]含まれています、 [!INCLUDE[ssDE](../includes/ssde-md.md)]、格納、処理、データ、レプリケーション、フルテキスト検索、リレーショナルを管理するためのツールと XML データをセキュリティで保護するため、データベース analytics との統合のためのコア サービスです。|  

**Developer、Enterprise コア、および Evaluation edition**  
Developer、Enterprise コア、および Evaluation edition でサポートされる機能、SQL Server Enterprise edition の次の表に示された機能を参照してください。

Developer Edition は引き続き [SQL Server 分散再生](../tools/distributed-replay/sql-server-distributed-replay.md) のクライアントを 1 つだけサポートします。 
  
##  <a name="Cross-BoxScaleLimits"></a> スケールの制限  
  
|機能|Enterprise|Standard|Web|Express| 
|-------------|----------------|--------------|---------|------------------------|
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限| 
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] または [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとのバッファー プールの最大メモリ|オペレーティング システムの最大容量|128 GB|64 GB|1410 MB|
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとの列ストア セグメント キャッシュの最大メモリ|メモリ制限なし| 32 GB| 16 GB| 352 MB|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のデータベースごとの最大メモリ最適化データ サイズ|メモリ制限なし| 32 GB| 16 GB| 352 MB|
|リレーショナル データベースの最大サイズ|524 PB|524 PB|524 PB|10 GB|  
  
<sup>1</sup> Enterprise edition with Server およびクライアント アクセス ライセンス (CAL) ベース ライセンス (新しい使用許諾契約は利用できません) は、最大で SQL Server インスタンスあたり 20 コアに制限されます。 コアベースのサーバー ライセンス モデルでは、制限はありません。 詳細については、次を参照してください。[エディションの SQL Server での計算容量制限](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)です。  
 
##  <a name="RDBMSHA"></a> RDBMS の高可用性  
  
|機能|Enterprise|Standard|Web|Express|  
|-------------|----------------|--------------|---------|------------------------|  
|ログ配布|はい|可|可|不可|  
|バックアップ圧縮|はい|可|いいえ|不可| 
|データベース スナップショット|可|いいえ|いいえ|不可|
|Always On フェールオーバー クラスター インスタンス<sup>1</sup>|可|可|いいえ|不可| 
|Always On 可用性グループ<sup>2</sup>|可|いいえ|いいえ|不可|
|基本的な可用性グループ<sup>3</sup>|不可|可|いいえ|不可|
|最小レプリカ コミット可用性グループ|はい|可|いいえ|不可|
|クラスターを使用しない可用性グループ|はい|可|いいえ|不可|
|オンライン ページおよびファイルの復元|はい|いいえ|いいえ|不可|
|オンラインのインデックス構築|はい|いいえ|いいえ|不可|
|再開可能なオンライン インデックス再構築|はい|いいえ|いいえ|不可|
|オンラインのスキーマ変更|はい|いいえ|いいえ|不可|
|高速復旧|はい|いいえ|いいえ|不可|
|ミラー化バックアップ|はい|いいえ|いいえ|不可|
|ホット アド メモリと CPU|はい|いいえ|いいえ|不可|
|暗号化されたバックアップ|はい|可|いいえ|不可|
|Windows Azure へのハイブリッド バックアップ (URL へのバックアップ)|はい|可|いいえ|不可|
  
<sup>1</sup> Enterprise edition、ノードの数はオペレーティング システムの最大値。 Standard Edition では、2 つのノードがサポートされます。 

<sup>2</sup>の Enterprise edition は、2 つの同期セカンダリ レプリカを含む、最大 8 個のセカンダリ レプリカのサポートを提供します。 

<sup>3</sup> standard edition には、基本的な可用性グループがサポートしています。 基本的な可用性グループは、1 つのデータベースで、2 つのレプリカをサポートします。 基本的な可用性グループの詳細については、「[基本的な可用性グループ](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md)」を参照してください。    

##  <a name="RDBMSSP"></a> RDBMS のスケーラビリティとパフォーマンス  
  
|機能|Enterprise|Standard|Web|Express|  
|-------------|----------------|--------------|---------|------------------------| 
|列ストア <sup>1</sup>|はい|可|可|はい|  
|クラスター化列ストア インデックス内のラージ オブジェクト バイナリ|はい|可|可|はい|  
|オンライン非クラスター化列ストア インデックスの再構築|はい|いいえ|いいえ|不可|
|インメモリ OLTP <sup>1</sup>|はい|可|可|はい|
|恒久的なメイン メモリ|はい|可|可|可|
|テーブルとインデックスのパーティション分割|はい|可|可|はい|  
|データ圧縮|はい|可|可|はい|
|[リソース ガバナー]|はい|いいえ|いいえ|不可|  
|パーティション テーブルの並列処理|はい|いいえ|いいえ|不可|
|NUMA 対応のラージ ページ メモリとバッファー配列の割り当て|はい|いいえ|いいえ|不可|
|IO リソース管理|はい|いいえ|いいえ|不可|  
|遅延持続性|はい|可|可|はい|
|自動調整|はい|いいえ|いいえ|不可|
|バッチ モードの適応型結合|はい|いいえ|いいえ|不可|
|バッチ モード メモリ許可フィードバック|可|いいえ|いいえ|不可|
|複数ステートメントのテーブル値関数のインターリーブ実行|可|可|可|可|
|一括挿入の機能強化|はい|可|可|はい|


<sup>1</sup> インメモリ OLTP データ サイズおよび列ストア セグメント キャッシュは、「スケールの制限」セクションでエディションごとに指定されているメモリ量に制限されます。 並列処理には最大限度があります。 プロセス (DOP) のインデックス構築の並列処理の次数は、Standard edition の 2 つの DOP と、Web edition および Express edition の DOP を 1 に制限されます。 これは、ディスク ベース テーブルとメモリ最適化テーブルで作成された列ストア インデックスに当てはまります。

##  <a name="RDBMSS"></a> RDBMS のセキュリティ  
  
|機能|Enterprise|Standard|Web|Express|
|-------------|----------------|--------------|---------|------------------------------------| 
|行レベルのセキュリティ|はい|可|可|はい|  
|Always Encrypted|はい|可|可|はい| 
|動的なデータ マスキング|はい|可|可|はい|   
|基本的な監査|はい|可|可|はい| 
|詳細な監査|はい|可|可|はい| 
|透過的なデータベースの暗号化|はい|いいえ|いいえ|不可|   
|ユーザー定義ロール|はい|可|可|はい| 
|包含データベース|はい|可|可|はい| 
|バックアップの暗号化|はい|可|いいえ|不可|  

##  <a name="RDBMSM"></a> RDBMS の管理の容易性  
  
|機能|Enterprise|Standard|Web|Express|   
|-------------|----------------|--------------|---------|------------------------|  
|専用管理者接続|はい|可|はい|可 (トレース フラグを使用)|可 (トレース フラグを使用)|   
|PowerShell スクリプティングのサポート|はい|可|可|はい| 
|データ層アプリケーション コンポーネントの操作のサポート - 抽出、配置、アップグレード、削除|はい|可|可|はい| 
|ポリシー オートメーション (変更時とスケジュールに基づいて確認)|はい|可|可|いいえ|不可|   
|パフォーマンス データ コレクター|はい|可|可|いいえ|不可| 
|標準的なパフォーマンス レポート|はい|可|可|いいえ|不可| 
|プラン ガイドおよびプラン ガイドの固定計画|はい|可|可|いいえ|不可|   
|NOEXPAND ヒントを使用したインデックス付きビューの直接クエリ|はい|可|可|はい| 
|インデックス付きビューの自動メンテナンス|はい|可|可|いいえ|不可| 
|分散パーティション ビュー|はい|いいえ|いいえ|不可| 
|並列インデックス操作|はい|いいえ|いいえ|不可|  
|クエリ オプティマイザーによる自動的なインデックス付きのビュー使用|はい|いいえ|いいえ|不可| 
|並列整合性チェック|はい|いいえ|いいえ|不可| 
|SQL Server ユーティリティ コントロール ポイント|はい|いいえ|いいえ|不可|    

##  <a name="Programmability"></a> Programmability  
  
|機能|Enterprise|Standard|Web|Express 
|-------------|----------------|--------------|---------|------------------------|  
|JSON|はい|可|可|はい|   
|クエリ ストア|はい|可|可|はい|   
|テンポラル|はい|可|可|はい|   
|ネイティブ XML サポート|はい|可|可|はい| 
|XML インデックスの作成|はい|可|可|はい| 
|MERGE と UPSERT の機能|はい|可|可|はい|   
|日付および時刻データ型|はい|可|可|はい|  
|国際化サポート|はい|可|可|はい| 
|フルテキストおよびセマンティック検索|はい|可|可|可|不可| 
|クエリ内の言語指定|はい|可|可|可|不可|   
|Service Broker (メッセージング)|はい|はい|不可 (クライアントのみ)|不可 (クライアントのみ)|不可 (クライアントのみ)|   
|Transact-SQL エンドポイント|はい|可|可|いいえ|不可| 
|グラフ|はい|可|可|はい|  


<sup>1</sup> 複数のコンピューティング ノードでのスケール アウトにはヘッド ノードが必要です。

## <a name="IS"></a> Integration Services

各エディションでサポートされている Integration Services (SSIS) の機能に関する情報の[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]を参照してください[Integration Services の機能が SQL Server のエディションでサポートされる](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md)です。

##  <a name="SLS"></a> 空間およびロケーション サービス  
  
|機能名|Enterprise|Standard|Web|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|空間インデックス|はい|可|可|はい|   
|平面データ型と測地データ型|はい|可|可|はい| 
|高度な空間的なライブラリ|はい|可|可|はい|   
|業界標準の空間データ形式のインポート/エクスポート|はい|可|可|可|   

  
## <a name="next-steps"></a>次の手順 
 [エディションと SQL Server 2017 - Windows でサポートされる機能](../sql-server/editions-and-components-of-sql-server-2017.md)  
 [エディションと SQL Server 2016 の Windows でサポートされる機能](../sql-server/editions-and-components-of-sql-server-2016.md)  
 [エディションと SQL Server 2014 の Windows でサポートされる機能](http://msdn.microsoft.com/library/cc645993(v=sql.120).aspx)  
 [SQL Server をインストールする](../database-engine/install-windows/installation-for-sql-server-2016.md)  
 [SQL Server の製品仕様](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb) 

  
  
