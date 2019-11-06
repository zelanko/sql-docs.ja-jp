---
title: 並列データ ウェアハウスのコンポーネント - Analytics Platform System |Microsoft Docs
description: この記事では、アプライアンスのソフトウェアと Analytics Platform System の非アプライアンス ソフトウェア コンポーネントについて説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 87525a741c1d0081b366394c0c5dd1b152ad15f1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960474"
---
# <a name="parallel-data-warehouse-components---analytics-platform-system"></a>並列データ ウェアハウスのコンポーネント - Analytics Platform System
この記事では、アプライアンスのソフトウェアと Analytics Platform System の非アプライアンス ソフトウェア コンポーネントについて説明します。  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![並列データ ウェアハウス ソフトウェア](media/parallel-data-warehouse-software.png "並列データ ウェアハウス ソフトウェア")  
  
## <a name="sec1"></a>アプライアンス ソフトウェア - クエリの処理とユーザーのデータ ストレージ  
  
### <a name="control-node"></a>制御ノード  
MPP エンジン  
MPP エンジンは、超並列処理 (MPP) システムの頭脳であります。 その後、次の処理を実行します。  
  
-   並列クエリ プランを作成し、コンピューティング ノードで並列クエリの実行を調整します。  
  
-   格納し、すべてのデータベースのメタデータと構成データを調整します。  
  
-   SQL Server PDW のデータベースの認証と承認を管理します。  
  
-   ハードウェアおよびソフトウェアの状態を追跡します。  
  
### <a name="data-movement-service-dms"></a>Data Movement Service (DMS)  
データ移動サービス (DMS) は、PDW の「秘密のソース」の一部です。 その後、次の処理を実行します。  
  
-   SQL Server PDW ノード間でデータを転送します。  
  
-   クエリ ノード間でデータの転送を必要とする操作を処理します。  
  
-   データ転送速度を最適化することによってクエリのパフォーマンスが向上します。  
  
### <a name="admin-console"></a>管理コンソール  
管理者コンソールは、アプライアンスの状態、ヘルス、およびパフォーマンス情報を提供する web アプリケーションです。  
  
### <a name="configuration-manager"></a>Configuration Manager  
Configuration Manager (dwconfig.exe) は、アプライアンス管理者 Analytics Platform System の構成に使用するツールです。  
  
### <a name="control-node-databases"></a>制御ノード データベース  
SQL Server では、すべての管理 ノードでデータベースを管理します。  
  
-   シェル データベースは、すべての分散のユーザー データベースのメタデータを管理します。  
  
-   TempDB には、アプライアンス間でのすべてのユーザーの一時テーブルのメタデータが含まれています。  
  
-   マスターは、制御ノードでの SQL Server のマスター テーブルです。  
  
### <a name="compute-node"></a>計算ノード  
コンピューティング ノードは、並列データ処理とストレージ ユニットです。 直接接続されたストレージがある、ユーザー データを管理する SQL Server を使用します。  
  
### <a name="data-movement-service-dms"></a>Data Movement Service (DMS)  
データ移動サービス (DMS) は、以下を行うには、各コンピューティング ノードで実行されます。  
  
-   並列クエリの処理の一環として、DMS とその他のコンピューター ノードと制御ノードからデータを転送します。  
  
-   各コンピューティング ノードで実行されている DMS は、並列のデータの読み込みを受信します。 コンピューティング ノードに並列的に読み込み、サーバーから直接データが読み込まれる  
  
-   DMS は、各コンピューティング ノードからバックアップ サーバーに直接データを転送します。  
  
-   PolyBase を使用して、DMS と外部の Hadoop クラスターまたは Azure Storage Blob からデータを転送します。  
  
### <a name="compute-node-databases"></a>コンピューティング ノード データベース 
各コンピューティング ノードでは、クエリを処理し、ユーザー データを管理する SQL Server のインスタンスを実行します。  
  
## <a name="appliance-fabric"></a>アプライアンス ファブリック  
アプライアンス ファブリックは、アプライアンスのオペレーティング システム、サービス、およびネットワーク インフラストラクチャを提供します。  
  
### <a name="domain-controller"></a>ドメイン コントローラー  
Active Directory (AD) Domain Services (DS)  
Analytics Platform System は、Analytics Platform System ノード間での認証を実行し、SQL Server PDW の Windows 認証ログインの認証を管理します。  
  
DNS サービス  
Windows ドメイン ネーム サービス (DNS) は、Analytics Platform System appliance の IP アドレスにドメイン名を解決します。  
  
### <a name="windows-deployment-service"></a>Windows 展開サービス  
Windows 展開サービス (WDS) は、アプライアンス上に Windows Server オペレーティング システムをデプロイします。 アプライアンスにわたってすべてのホストと仮想マシンに展開します。  
  
DHCP サービスは、IP アドレスを作成するため、アプライアンスのドメイン内のホスト事前構成済みの IP アドレスをしなくても、アプライアンスのネットワークに参加できます。  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Analytics Platform System は、高可用性を実現するために、仮想化を使用します。 Virtual Machine Manager は、物理ホスト上のオペレーティング システムを展開する System Center をホストします。  
  
Windows Server Update Services (WSUS) を適用またはすべてのホストとバーチャル マシンで Windows 更新プログラムを削除します。  
  
### <a name="windows-server"></a>Windows Server  
すべてのホストと、アプライアンスの仮想マシンは、Windows Server オペレーティング システムを実行します。  
  
### <a name="failover-clustering"></a>フェールオーバー クラスタリング  
Windows フェールオーバー クラスタ リング、ホストが失敗したことに、パッシブ ホスト上のプロセスを再起動する機能を提供します。  
  
### <a name="storage-spaces"></a>記憶域スペース  
Windows 記憶域スペースは、コンピューティング ノードの小規模なグループの記憶域プールとして、ユーザー データを管理します。 コンピューティング ノードが失敗した場合、データは、グループ内の別のコンピューティング ノード経由でアクセスできます。  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft HYPER-V Server では、シンプルで信頼性の高い仮想化ソリューションを提供します。 Analytics Platform System は、CPU リソースのバランスを取る、fabric のコンポーネントの PDW ノードとアプライアンスの高可用性を実現する、仮想化を使用します。  
  
## <a name="sec2"></a>非リレーショナル データ
PolyBase テクノロジは、外部の Hadoop データと SQL Server の PDW データを統合します。 これらの Hadoop データ ソースのいずれかでは、Hadoop データを格納できます。  
  
-   Hortonworks の Hadoop ディストリビューション  
  
-   Hadoop の Cloudera ディストリビューション  
  
-   Azure Storage Blob に格納されている HDInsight データ  
  
## <a name="query-tools"></a>クエリ ツール   
  
クエリは、Transact と共に書き込ま\-SQL クエリの MPP 特性に合わせて変更します。 すべてのクエリは、コンピューティング ノード間でクエリを実行する並列クエリ プランを生成するコントロールのノードに送信されます。  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools は Visual Studio 内で実行しは SQL Server PDW にクエリを送信するための推奨される、GUI ツールです。 オブジェクト エクスプ ローラー内を移動することによって SQL Server Management Studio に似ています。  
  
Visual Studio がまだしていない場合は、無料の必要なツールをダウンロードできます。 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>sqlcmd コマンド ライン クエリ ツール  
sqlcmd はトランザクションを実行するための SQL Server コマンド ライン ツール\-SQL ステートメントやシステム コマンド。 SQL Server PDW で動作しは SQL Server PDW のクエリを実行するための推奨される、コマンド ライン ツールです。 Sqlcmd を使用したトランザクションを実行することができます\-バッチ ファイルとして、コマンドラインから対話形式で、または Windows PowerShell から SQL ステートメント。  
  
<!-- MISSING LINKS

If you don't have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Integration Services  
SQL Server PDW のクエリには、Integration Services を使用できます。 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Linked Server  
トランザクションを送信する SQL Server を使用する SQL Server のリンクされたサーバーの接続を使用すると、\-SQL Server PDW に SQL ステートメント。 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>ビジネス インテリジェンス ツール
  
### <a name="analysis-services"></a>Analysis Services  
SQL Server PDW は、Analysis Services データベースおよび Excel の PowerPivot モデルの有効なデータ ソースです。 OLE DB プロバイダーを使用すると、多次元オンライン分析処理 (MOLAP) またはリレーショナル オンライン分析処理 (ROLAP) ストレージを使用して、Analysis Services キューブを構成できます。  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>レポート ビルダー  
SQL Server PDW は、SQL Server レポート ビルダーを使用して Reporting Services を開発するレポートの SQL Server のデータ ソースとして使用できます。 SQL Server のソースとしてレポート モデルの SQL Server PDW を使用することもできます。 レポート マネージャーまたはレポート サーバーの API を使用して、SQL Server PDW のデータベースからモデルを生成できます。  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot for Excel  
PowerPivot での SQL Server PDW に接続するには、excel、Excel のデータ分析機能を大幅に拡張を無料でダウンロードします。  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>読み込みツール 
  
### <a name="integration-services"></a>Integration Services  
SQL Server PDW にデータを読み込む SQL ServerIntegration サービスを使用するための PDW に固有の変換先アダプターをインストールします。  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>dwloader のコマンドラインのローダー  
dwloader は、読み込みサーバーから、SQL Server PDW のコンピューティング ノードに並列でのデータを読み込むのコマンドライン読み込みツールです。 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>PolyBase は Hadoop の統合  
SQL Server PDW のリレーショナル テーブルに PolyBase テクノロジで、Hadoop クラスター非リレーショナル データを読み込むことができます。 Hadoop のデータは外部の Hadoop クラスターまたは Azure Storage Blob に存在することはできます。  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>データベースのバックアップと復元  
SQL Server PDW は、Transact SQL データベースのバックアップを使用し、バックアップにコマンドを復元し、バックアップ サーバーとの間に並列でのユーザー データベースを復元します。 SQL Server PDW では、Windows ファイル共有、ディレクトリにバックアップを書き込み、同様に、データを Windows ファイル共有から復元します。  
  
詳細については、次を参照してください[のバックアップと読み込みハードウェア計画](backup-and-loading-hardware.md)と[バックアップと復元の概要。](backup-and-restore-overview.md)  
  
## <a name="remote-table-copy"></a>リモート テーブルのコピー  
リモート テーブル コピー機能 (非アプライアンス) のリモートの SMP SQL Server データベースの SQL Server PDW のデータベースからテーブルをコピーすることができます。 これにより、SQL Server PDW のハブとスポークのシナリオ。  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>監視  
Analytics Platform System はアプライアンスのアクティビティを監視するいくつかの方法  
  
### <a name="admin-console"></a>管理コンソール  
管理コンソールを使用すると、アプライアンスの正常性に関する現在の状態を表示できます。 これにより、制御ノードで web アプリケーションとして実行されが https 経由でアクセス可能です。  
  
詳細については、次を参照してください[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System。&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>システム ビュー  
管理コンソールは、システム ビューのクエリに基づいています。 必要な情報の特定の部分を取得するには、個別にシステム ビューを照会できます。  

詳細については、次を参照してください[システム ビューを使用して、アプライアンスの監視&#40;Analytics Platform System。&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
SQL Server PDW の System Center Operations Manager (SCOM) 管理パックがあります。 

SCOM でのアプライアンスを構成するを参照してください[System Center Operations Manager を使用して、アプライアンスの監視&#40;Analytics Platform System。&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
