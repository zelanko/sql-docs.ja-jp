---
title: 並列データ ウェアハウスの概要
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: このトピックでは、アプライアンス ソフトウェアおよび Analytics Platform System のアプライアンス以外のソフトウェア コンポーネントについて説明します。
ms.date: 01/05/2017
ms.topic: article
ms.assetid: db0c4a43-a66d-4c44-ab91-791c5785f71c
caps.latest.revision: 20
ms.openlocfilehash: 42fb92c30c0487603f2ad8e870886f25b4c1655a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="parallel-data-warehouse-overview"></a>並列データ ウェアハウスの概要
このトピックでは、アプライアンス ソフトウェアおよび Analytics Platform System のアプライアンス以外のソフトウェア コンポーネントについて説明します。  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![並列データ ウェアハウス ソフトウェア](media/parallel-data-warehouse-software.png "Parallel Data Warehouse ソフトウェア")  
  
## <a name="sec1"></a>アプライアンス ソフトウェア – クエリの処理とユーザーのデータ ストレージ  
  
### <a name="control-node"></a>コントロールのノード  
MPP エンジン  
MPP エンジンは、膨大な並列処理 (MPP) システムの頭脳です。 その後、次の処理を実行します。  
  
-   並列クエリ プランを作成し、コンピューティング ノードで並列クエリの実行を調整します。  
  
-   格納し、すべてのデータベースのメタデータと構成データを調整します。  
  
-   SQL Server PDW のデータベースの認証と承認を管理します。  
  
-   ハードウェアおよびソフトウェアの状態を追跡します。  
  
### <a name="data-movement-service-dms"></a>データ移動サービス (DM)  
データ移動サービス (DM) は、PDW の「秘密ソース」の一部です。 その後、次の処理を実行します。  
  
-   SQL Server PDW ノード間でデータを転送します。  
  
-   ノード間でデータの転送を必要とする操作のクエリを処理します。  
  
-   データ転送速度を最適化することによってクエリのパフォーマンスが向上します。  
  
### <a name="admin-console"></a>管理コンソール  
管理者コンソールは、アプライアンスの状態、ヘルス、およびパフォーマンス情報を表示する web アプリケーションです。  
  
### <a name="configuration-manager"></a>構成マネージャー  
Configuration Manager (dwconfig.exe) は、分析プラットフォーム システムを構成するアプライアンス管理者を使用するツールです。  
  
### <a name="control-node-databases"></a>コントロールのノードのデータベース  
SQL Server では、すべての管理 ノードでデータベースを管理します。  
  
-   シェル データベースは、すべての分散のユーザー データベースのメタデータを管理します。  
  
-   TempDB には、アプライアンスにわたってのすべてのユーザーの一時テーブルのメタデータが含まれています。  
  
-   マスターは、コントロールのノードに SQL Server のマスター テーブルです。  
  
### <a name="compute-node"></a>コンピューティング ノード  
コンピューティング ノードには、並列データ処理および記憶域ユニットです。 直接接続されたストレージと SQL Server を使用してユーザー データを管理します。  
  
### <a name="data-movement-service-dms"></a>データ移動サービス (DM)  
データ移動サービス (DM) は、以下を行うには、各コンピューティング ノード上で実行します。  
  
-   並列クエリの処理の一環として、DMS は他のコンピューター ノードおよび [管理] ノードの間のデータを転送します。  
  
-   各コンピューティング ノードで実行されている DMS は、並列のデータが読み込まれたを受け取ります。 並列読み込みサーバーから直接、コンピューティング ノードにデータが読み込まれる  
  
-   DMS は、各コンピューティング ノードからデータをバックアップ サーバーに直接転送します。  
  
-   PolyBase を使用して、DMS は、アプライアンス上の外部の Hadoop クラスター、または HDInsight リージョン間でデータを転送します。  
  
### <a name="compute-node-databases"></a>コンピューティング ノードのデータベース 
各コンピューティング ノードでは、クエリを処理し、ユーザー データを管理する SQL Server のインスタンスを実行します。  
  
## <a name="appliance-fabric"></a>アプライアンス ファブリック  
アプライアンス ファブリックは、アプライアンスのオペレーティング システム、サービス、およびネットワーク インフラストラクチャを提供します。  
  
### <a name="domain-controller"></a>ドメイン コントローラー  
Active Directory (AD) ドメイン サービス (DS)  
Analytics Platform System は、Analytics Platform System ノード間での認証を実行し、SQL Server PDW の Windows 認証のログインの認証を管理します。  
  
DNS サービス  
Windows ドメイン ネーム サービス (DNS) は、ドメイン名を Analytics Platform System アプライアンスの IP アドレスに解決します。  
  
### <a name="windows-deployment-service"></a>Windows 展開サービス  
Windows 展開サービス (WDS) では、アプライアンス上に Windows Server オペレーティング システムを展開します。 これについては、アプライアンスにわたってすべてのホストとバーチャル マシンに展開されます。  
  
DHCP サービスは、事前構成済みの IP アドレスをしなくてもアプライアンス ネットワークに参加することができます、アプライアンス ドメイン内でホストされるように、IP アドレスを作成します。  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Analytics Platform System は、高可用性を実現するために、仮想化を使用します。 Virtual Machine Manager は、物理ホスト上のオペレーティング システムを展開する System Center をホストします。  
  
Windows Server Update Services (WSUS) を適用またはすべてのホストとバーチャル マシン間での Windows 更新プログラムを削除します。  
  
### <a name="windows-server"></a>Windows Server  
すべてのホストとアプライアンス内の仮想マシンは、Windows Server オペレーティング システムを実行します。  
  
### <a name="failover-clustering"></a>フェールオーバー クラスタリング  
Windows フェールオーバー クラスタ リングは、ホストが失敗した場合にパッシブ ホスト上のプロセスを再開する機能を提供します。  
  
### <a name="storage-spaces"></a>記憶域スペース  
Windows 記憶域スペースは、コンピューティング ノードの小規模なグループの記憶域プールとして、ユーザー データを管理します。 コンピューティング ノードが失敗した場合、データは、グループ内の別のコンピューティング ノード経由でアクセスできます。  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft HYPER-V Server は、シンプルで信頼性の高い仮想化ソリューションを提供します。 Analytics Platform System は、CPU リソースのバランスをとるとファブリック コンポーネント PDW ノードとアプライアンスの高可用性を実現する、仮想化を使用します。  
  
## <a name="sec2"></a>非リレーショナル データ
外部の Hadoop データと SQL Server PDW のデータを統合する PolyBase テクノロジ。 Hadoop のデータは、これらの Hadoop データ ソースのいずれかに格納できます。  
  
-   Hortonworks for Linux または Windows Server  
  
-   Linux 上の Cloudera  
  
-   APS で実行されている HDInsight  
  
-   Azure Storage の Blob に格納されている HDInsight データ  
  
## <a name="query-tools"></a>クエリ ツール   
  
クエリは、Transact と共に書き込ま\-SQL クエリの MPP 性質に合わせて変更します。 すべてのクエリは、コンピューティング ノード間でクエリを実行する並列クエリ プランを生成するコントロールのノードに送信されます。  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools は Visual Studio 内で実行し、SQL Server PDW にクエリを実行するための推奨される、GUI ツールです。 オブジェクト エクスプ ローラー内を移動することによって SQL Server Management Studio に似ています。  
  
既に Visual Studio を持っていない場合は、無料で必要なツールをダウンロードできます。 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>sqlcmd コマンド ライン クエリ ツール  
sqlcmd は Transact を実行するための SQL Server コマンド ライン ツール\-SQL ステートメントやシステム コマンド。 SQL Server PDW で動作し、SQL Server PDW のクエリを実行するための推奨される、コマンド ライン ツールです。Sqlcmd では、Transact を実行することができます\-バッチ ファイルとして、コマンドラインから対話的にまたは Windows PowerShell から SQL ステートメント。  
  
<!-- MISSING LINKS

If you don’t have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Integration Services  
SQL Server PDW のクエリには、Integration Services を使用できます。 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Linked Server  
Transact を送信する SQL Server を使用する SQL のリンクされたサーバー接続を使用すると、\-SQL Server PDW に SQL ステートメント。 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>ビジネス インテリジェンス ツール
  
Analysis Services  
SQL Server PDW は、Analysis Services データベースおよび Excel PowerPivot モデル用の有効なデータ ソースです。 OLE DB プロバイダーを使用して、多次元オンライン分析処理 (MOLAP) またはリレーショナル オンライン分析処理 (ROLAP) ストレージを使用する Analysis Services キューブを構成することができます。  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>レポート ビルダー  
SQL Server PDW は、Reporting Services 用 SQL Server レポート ビルダーを使用して開発するレポートの SQL Server データ ソースとして使用できます。 レポート モデルの SQL Server のソースとして SQL Server PDW を使用することもできます。 レポート マネージャーまたはレポート サーバー API を使用すると、SQL Server PDW のデータベースからモデルを生成できます。  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot for Excel  
For Excel で Excel のデータ分析機能を大幅に拡張を無料でダウンロード PowerPivot での SQL Server PDW に接続することができます。  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>読み込みツール 
  
### <a name="integration-services"></a>Integration Services  
SQL Server PDW にデータを読み込む SQL ServerIntegration Services を使用できるように PDW に固有の変換先アダプターをインストールします。  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>dwloader のコマンド ライン ローダー  
dwloader は、データを読み込む並列読み込みサーバーからの SQL Server PDW のコンピューティング ノードに読み込みコマンド ライン ツールです。 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>PolyBase は Hadoop の統合  
PolyBase テクノロジを使用する SQL Server PDW のリレーショナル テーブルに、Hadoop クラスターからの非リレーショナル データを読み込むことができます。 Hadoop のデータは、外部の Hadoop クラスターの AP の HDI リージョンまたは Azure Storage の Blob に配置できます。  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>データベースのバックアップと復元  
SQL Server PDW 使用 Transact\-SQL データベースのバックアップと、バックアップおよびバックアップ サーバーとの間に、並列で、ユーザー データベースを復元するコマンドを復元します。 SQL Server PDW は、ディレクトリを Windows ファイル共有にバックアップを書き込み、同様に、データを Windows ファイル共有から復元します。  
  
詳細については、次を参照してください[のバックアップとハードウェアの読み込みの計画](backup-and-loading-hardware.md)と[バックアップと復元の概要。](backup-and-restore-overview.md)  
  
## <a name="remote-table-copy"></a>リモート テーブルのコピー  
リモート テーブルのコピー機能では、SQL Server PDW のデータベースからテーブルをリモートの (非アプライアンス) SMP SQL Server データベースにコピーすることができます。 これは、SQL Server PDW のハブとスポークのシナリオを実現できます。  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>監視  
Analytics Platform System がアプライアンス アクティビティを監視するいくつかの方法  
  
### <a name="admin-console"></a>管理コンソール  
管理コンソールでは、アプライアンスの正常性に関する現在の状態を表示することができます。 これにより、コントロールのノードで web アプリケーションとして実行れ、https 経由でアクセス可能です。  
  
詳細については、次を参照してください[アプライアンスを管理コンソールを使用して監視&#40;分析プラットフォーム システム。&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>システム ビュー  
管理コンソールは、システム ビューのクエリに基づいています。 特定の必要な情報を取得するには、個別に、システム ビューを照会できます。  

詳細については、次を参照してください[監視システム ビューを使用してアプライアンス&#40;分析プラットフォーム システム。&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
SQL Server PDW の System Center Operations Manager (SCOM) 管理パックがあります。 

SCOM のアプライアンスを構成するを参照してください[System Center Operations Manager を使用してアプライアンスをモニター&#40;分析プラットフォーム システム。&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
