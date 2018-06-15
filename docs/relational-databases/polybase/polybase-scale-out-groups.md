---
title: PolyBase スケールアウト グループ | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: polybase
ms.reviewer: ''
ms.suite: sql
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PolyBase
- PolyBase, scale-out groups
- scale-out PolyBase
ms.assetid: c7810135-4d63-4161-93ab-0e75e9d10ab5
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3fd249645266a7d9477e2dc098817138d8f722d0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34334333"
---
# <a name="polybase-scale-out-groups"></a>PolyBase スケールアウト グループ
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  PolyBase を使用するスタンドアロンの SQL Server インスタンスは、Hadoop または Azure BLOB ストレージの大量のデータ セットを処理する場合、パフォーマンス ボトルネックになる可能性があります。 PolyBase グループ機能では、Hadoop や Azure BLOB ストレージなどの外部データ ソースからの大量のデータ セットを、クエリ パフォーマンスの向上のためにスケールアウト形式で処理するために、SQL Server インスタンス クラスターを作成することができます。  
  
 「 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md) 」および「 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)」を参照してください。  
  
 ![PolyBase スケールアウト グループ](../../relational-databases/polybase/media/polybase-scale-out-groups.png "PolyBase スケールアウト グループ")  
  
## <a name="overview"></a>概要  
  
### <a name="head-node"></a>ヘッド ノード  
 ヘッド ノードには、PolyBase クエリの送信先の SQL Server インスタンスが含まれています。 各 PolyBase グループは、ヘッド ノードを 1 つだけ保持できます。 ヘッド ノードは、SQL Server インスタンス上の SQL データベース エンジン、PolyBase エンジン、および PolyBase データ移動サービスの論理グループです。  
  
### <a name="compute-node"></a>コンピューティング ノード  
 コンピューティング ノードには、外部データに対するスケールアウト クエリ処理を支援する SQL Server インスタンスが含まれています。 コンピューティング ノードは、SQL Server インスタンス上の SQL Server と PolyBase データ移動サービスの論理グループです。 PolyBase グループは、複数のコンピューティング ノードを保持できます。  ヘッド ノードとコンピューティング ノードはすべて、同じバージョンの SQL Server を実行する必要があります。
  
### <a name="distributed-query-processing"></a>分散クエリ処理  
 PolyBase クエリは、ヘッド ノード上の SQL Server に送信されます。 外部テーブルを参照するクエリの一部は、PolyBase エンジンに渡されます。  
  
 PolyBase エンジンは、PolyBase クエリの背後にある重要なコンポーネントです。 外部データに対するクエリを解析し、クエリ プランを生成して、作業を実行するためにコンピューティング ノード上のデータ移動サービスに配布します。 作業が完了すると、コンピューティング ノードから結果を受信し、この結果を処理してクライアントに返すために SQL Server に送信します。  
  
 PolyBase データ移動サービスは、PolyBase エンジンから指示を受信し、HDFS と SQL Server の間、およびヘッド ノードとコンピューティング ノード上の SQL Server インスタンス間でデータを転送します。  
  
### <a name="editions-availability"></a>エディションの可用性  
 SQL Server をセットアップしたら、インスタンスをヘッド ノードとコンピューティング ノードのどちらかとして指定できます。  指定できるノードは、実行されている SQL Server PolyBase のバージョンによって異なります。 Enterprise Edition インストールでは、インスタンスをヘッド ノードとコンピューティング ノードのどちらかとして指定できます。 Standard Edition では、インスタンスをコンピューティング ノードとしてのみ指定できます。  
  
## <a name="to-configure-a-polybase-group"></a>PolyBase グループを構成するには  
  
### <a name="prerequisites"></a>Prerequisites  
  
-   同じドメイン内の N 台のマシン  
  
-   PolyBase サービスを実行するドメイン ユーザー アカウント  
  
### <a name="steps"></a>手順  
  
1.  N 台のマシンに、同じバージョンの SQL Server と PolyBase をインストールします。  
  
2.  1 つの SQL Server インスタンスをヘッド ノードとして選択します。 ヘッド ノードは、SQL Server Enterprise を実行するインスタンスでのみ指定できます。  
  
3.  [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md) を使用して、残りの SQL Server インスタンスをコンピューティング ノードとして追加します。  
  
4.  [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md) を使用して、グループのノードを監視します。  
  
5.  省略可。 [sp_polybase_leave_group &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md) を使用して、コンピューティング ノードを削除します。  
  
## <a name="example-walk-through"></a>サンプル チュートリアル  
 ここでは、次のものを使用して PolyBase グループを構成する手順について説明します。  
  
1.  ドメイン *PQTH4A* 内の 2 つのマシン。マシン名は次のとおりです。  
  
    -   PQTH4A-CMP01  
  
    -   PQTH4A-CMP02  
  
2.  ドメイン アカウント: *PQTH4A\PolybaseUser*  
  
#### <a name="step-1-install-sql-server-with-polybase-on-all-machines"></a>手順 1: すべてのマシンに、PolyBase を使用する SQL Server をインストールする  
  
1.  setup.exe を実行します。  
  
2.  [機能の選択] ページで、 **[外部データ用 PolyBase クエリ サービス]** を選択します。  
  
3.  [サーバーの構成] ページで、SQL Server PolyBase エンジンと SQL Server PolyBase データ移動サービス用に **ドメイン アカウント** PQTH4A\PolybaseUser を使用します。  
  
4.  [PolyBase の構成] ページで、 **[PolyBase スケール アウト グループの一部として、SQL Server インスタンスを使用します]** オプションを選択します。 これにより、ファイアウォールが開かれて、PolyBase サービスへの着信接続が許可されます。  
  
5.  セットアップが完了したら、 **services.msc**を実行します。 SQL Server、PolyBase エンジン、および PolyBase データ移動サービスが実行されていることを確認します。  
  
     ![PolyBase サービス](../../relational-databases/polybase/media/polybase-services.png "PolyBase サービス")  
  
#### <a name="step-2-select-one-sql-server-as-head-node"></a>手順 2: 1 つの SQL Server をヘッド ノードとして選択する  
  
-   セットアップが完了すると、両方のマシンが PolyBase グループのヘッド ノードとして機能できます。 この例では、PQTH4A-CMP01 上の "MSSQLSERVER" をヘッド ノードとして選択します。  
  
#### <a name="step-3-add-other-sql-server-instances-as-compute-nodes"></a>手順 3: その他の SQL Server インスタンスをコンピューティング ノードとして追加する  
  
1.  PQTH4A-CMP02 上の SQL Server に接続します。  
  
2.  ストアド プロシージャ [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md)を実行します。  
  
    ```  
    -- Enter head node details:   
    -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';  
  
    ```  
  
3.  コンピューティング ノード (PQTH4A-CMP02) で、services.msc を実行します。  
  
4.  PolyBase エンジンをシャット ダウンし、PolyBase データ移動サービスを再起動します。  
  
#### <a name="optional-remove-a-compute-node"></a>省略可能: コンピューティング ノードを削除する  
  
1.  コンピューティング ノードの SQL Server (PQTH4A-CMP02) に接続します。  
  
2.  ストアド プロシージャ sp_polybase_leave_group を実行します。  
  
    ```  
    EXEC sp_polybase_leave_group;  
    ```  
  
3.  削除するコンピューティング ノード (PQTH4A-CMP02) で、services.msc を実行します。  
  
4.  PolyBase エンジンを起動します。 PolyBase データ移動サービスを再起動します。  
  
5.  PQTH4A-CMP01 で DMV sys.dm_exec_compute_nodes を実行して、ノードが削除されたことを確認します。 これで、PQTH4A-CMP02 はスタンドアロンのヘッド ノードとして機能するようになります。  
  
## <a name="next-steps"></a>次の手順  
 トラブルシューティングについては、「 [PolyBase troubleshooting with dynamic management views](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)   
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)   
 [PolyBase Connectivity Configuration &#40;Transact-SQL&#41; (PolyBase 接続性構成 (Transact-SQL))](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)  
  
  
