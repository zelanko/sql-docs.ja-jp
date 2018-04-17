---
title: 一括コピー バッチ サイズを管理する |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3c9f5d75a408da45aa5f00f7949f8e66d5abd8ef
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="managing-bulk-copy-batch-sizes"></a>一括コピー バッチ サイズの管理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一括コピー操作でバッチを使用する主な目的は、トランザクションのスコープを定義することです。 一括コピー関数では、バッチ サイズが設定されていないと、一括コピー全体を 1 つのトランザクションと見なします。 バッチ サイズが設定されている場合、各バッチはそのバッチの終了時にコミットされるトランザクションで構成されます。  
  
 バッチ サイズを指定せずに一括コピーを実行し、エラーが発生した場合は、一括コピー全体がロールバックされます。 実行時間が長い一括コピーの復旧には時間がかかることがあります。 バッチ サイズを設定すると、各バッチが 1 つのトランザクションと見なされ、各バッチがコミットされます。 エラーが発生した場合は、最後の未解決のバッチだけがロールバックされます。  
  
 バッチ サイズは、ロックのオーバーヘッドにも影響を与えることがあります。 に対して一括コピーを実行するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、TABLOCK ヒントを使用して指定できます[bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)行ロックではなくテーブル ロックを取得します。 1 つのテーブル ロックを設定すると、一括コピー操作全体のオーバーヘッドを最小限に抑えることができます。 TABLOCK を指定しないと各行がロックされるので、一括コピーの実行中にすべてのロックを保持するオーバーヘッドにより、パフォーマンスが低下することがあります。 トランザクションの長さだけロックが保持されるので、バッチ サイズを指定すると、定期的にコミットが発生して、その時点で保持されているロックが解放されるため、この問題を解決できます。  
  
 大量の行を一括コピーする場合、1 つのバッチを構成する行数がパフォーマンスに大きな影響を与えることがあります。 推奨バッチ サイズは、実行する一括コピーの種類によって異なります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への一括コピーを行う場合は、TABLOCK 一括コピー ヒントを指定し、大きなバッチ サイズを設定します。  
  
-   TABLOCK を指定しない場合は、バッチ サイズを 1,000 行未満に制限します。  
  
 呼び出して、バッチ サイズが指定された一括コピーするときに、データ ファイルから、 **bcp_control**呼び出す前に BCPBATCH オプションを使用して[bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)です。 一括を使用してプログラム変数からコピーする場合[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)と[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)、呼び出すことにより、バッチ サイズを制御[bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)呼び出した後[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x*回*x*バッチ内の行の数です。  
  
 バッチはトランザクションのサイズを指定するだけでなく、ネットワーク経由でサーバーに行を送信するときにも影響を与えます。 一括コピー関数は通常の行をキャッシュ**bcp_sendrow**ネットワーク パケットには、サーバーに、完全なパケットを送信するまでです。 アプリケーションを呼び出すと**bcp_batch**、しかし、現在のパケットがいっぱいになったかどうかに関係なく、サーバーに送信されます。 バッチ サイズを非常に小さくすると、いっぱいになっていないパケットが大量にサーバーに送信されるので、パフォーマンスが低下することがあります。 たとえば、呼び出し**bcp_batch**後すべて**bcp_sendrow**個別のパケットで送信される各行発生して、行が非常に大きく、しない限り、各パケット内の領域が無駄になります。 アプリケーションが呼び出すことによって、サイズを変更できますが、SQL Server のネットワーク パケットの既定のサイズは 4 KB で[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)から SQL_ATTR_PACKET_SIZE 属性を指定します。  
  
 バッチの別の副作用は、各バッチが未解決の結果セットを完了するまでと見なされる**bcp_batch**です。 バッチが未解決、中に、接続ハンドルで他の操作が試行された場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー エラーが発生 sqlstate ="HY000"のエラー メッセージ文字列。  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a>参照  
 [一括コピー操作を実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
