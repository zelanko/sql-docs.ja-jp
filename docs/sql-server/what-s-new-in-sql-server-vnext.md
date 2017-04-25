---
title: "SQL Server vNext の新機能 | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-vnext
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: craigg-msft
ms.author: craigg
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f4a9065cccb31a8ee71e142aeba054addd6c4a5d
ms.lasthandoff: 04/11/2017

---
# <a name="what39s-new-in-sql-server-vnext"></a>SQL Server vNext の新機能
SQL Server vNext は、SQL Server のパワーを Linux、Linux ベースの Docker コンテナー、Windows に届けることで、SQL Server を開発言語、データ型、オンプレミス/クラウドの選択が可能で、オペレーション システムに依存しないプラットフォームにするための大きな一歩です。

このトピックでは、最新の Community Technical Preview (CTP) リリースの新機能の概要、各機能領域の新しい情報が詳しく記載されたリンクについて説明します。

![info_tip](../sql-server/media/info-tip.png) SQL Server を Linux で実行できます。 詳細については、以下をご覧ください。
-  [Linux の SQL Server vNext の新機能](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-whats-new)
-  [SQL Server on Linux ドキュメント](https://docs.microsoft.com/en-us/sql/linux/)


**お試しください:**    
   -   [![Download from Evaluation Center](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) **[Download the SQL Server vNext Community Technology Preview](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="whats-new-in-sql-server-vnext-ctp-14-march-2017"></a>SQL Server vNext CTP 1.4 の新機能 (2017 年 3 月)
### <a name="sql-server-database-engine"></a>SQL Server データベース エンジン
- この CTP に新しいデータベース エンジン機能はありません。
- この CTP にはデータベース エンジンのバグ修正が含まれています。
- 前回の CTP リリースでの vNext CTP の機能強化の詳細な一覧については、「 [SQL Server vNext の新機能 (データベース エンジン)](../database-engine/configure-windows/what-s-new-in-sql-server-vnext-database-engine.md)」を参照してください。

### <a name="sql-server-r-services"></a>SQL Server R サービス
- この CTP に新しい R Services 機能はありません。
- 以前の CTP の詳細など、R Services の新しい情報については、「 [SQL Server R Services の新機能](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md)」を参照してください。  

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- この CTP に新しい SSRS 機能はありません。
- 以前のリリースの詳細など、SSRS の新しい情報については、「 [Reporting Services の新機能 (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)」を参照してください。 

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)
- この CTP に新しい SSAS 機能はありません。  
- 最新版の SSDT と SSMS プレビュー リリースにおける Analysis Services の新機能などの詳細については、「[What's New in Analysis Services vNext](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md) (Analysis Services vNext の新機能)」を参照してください。  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- この CTP に新しい SSIS 機能はありません。
- 以前の CTP の詳細など、SSIS の新しい情報については、「 [What's New in Integration Services vNext](../integration-services/what-s-new-in-integration-services-in-sql-server-vnext.md)」(Integration Services vNext の新機能) を参照してください。  

### <a name="master-data-services-mds"></a>マスター データ サービス (MDS)
- この CTP に新しいマスター データ サービス機能はありません。

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-vnext-ctp-13-february-2017"></a>SQL Server vNext CTP 1.3 の新機能 (2017 年 2 月)
### <a name="sql-server-database-engine"></a>SQL Server データベース エンジン
- 間接チェックポイントのパフォーマンスが強化されました。
- クラスターレス可用性グループのサポートが追加されました。
- ミニマム レプリカ コミット可用性グループの設定が追加されました。
- Windows と Linux 間で可用性グループが利用できるようになり、OS 間での移行とテストができるようになりました。
- テンポラル表の保持ポリシーのサポートが追加されました。
- DMV SYS.DM_DB_STATS_HISTOGRAM が新しくなりました。
- 非クラスター化列ストア インデックスのオンライン ビルドおよびリビルドのサポートが追加されました。
- Linux プロセスの情報を返す動的管理ビューが&5; つ追加されました。 詳細については、 [Linux のサービスの動的管理ビュー](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md)に関する記事を参照してください。   
- 統計情報を確認するための[sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) が追加されました。

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>SQL Server Analysis Services (SSAS) (CTP 1.3)
- エンコードのヒント。これは、大規模なメモリ内のテーブル モデルの処理 (データの更新) を最適化するために使用される高度な機能です。 詳細については、「 [SQL Server Analysis Services vNext の新機能](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md)」を参照してください。 


![horizontal_bar](../sql-server/media/horizontal-bar.png)

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) SQL Server エンジニアリング チームと連携する 
- [スタック オーバーフロー (tag sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - バグ報告と機能依頼](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - R に関する一般的なディスカッション](https://www.reddit.com/r/SQLServer/)

## <a name="see-also"></a>参照    
 + [![リリース ノート](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png)] [SQL Server VNext リリース ノート](../sql-server/sql-server-vnext-release-notes.md) 
+ [SQL Server&2016; の各エディションとサポートされる機能](https://msdn.microsoft.com/library/cc645993.aspx)
 + [SQL Server&2016; のインストールに必要なハードウェアおよびソフトウェア](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
 + [インストール ウィザードからの SQL Server&2016; のインストール (セットアップ)](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)
 
 + [セットアップとサービスのインストール](http://msdn.microsoft.com/library/6df72a78-6b36-4bc1-948e-04b4ebe46094)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)



