---
title: "データ ソースからの切断 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-communication
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
caps.latest.revision: "31"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3dd797c1a011549fdae5e3fb9ee20e95875c9634
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="disconnecting-from-a-data-source"></a>データ ソースからの切断
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションは、データ ソースの使用が完了したら、それを呼び出す**SQLDisconnect**です。 **SQLDisconnect**接続に割り当てられているすべてのステートメントを解放し、データ ソースからドライバーを切断します。 切断後、アプリケーションが呼び出すことができます[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)接続ハンドルを解放します。 アプリケーションを終了する前に呼び出すも**SQLFreeHandle**環境ハンドルを解放します。  
  
 切断後は、割り当てられていた接続ハンドルを再利用して、別のデータ ソースに接続したり、同じデータ ソースに再接続したりできます。 切断してから後で再接続するか、接続した状態を維持するかを決める際、アプリケーションの作成者は各操作の相対コストを考慮する必要があります。 接続メディアによっては、データ ソースに接続し、接続した状態を維持するのに比較的コストがかかる場合があります。 両者を比較検討する場合は、アプリケーションで同じデータ ソースに追加操作が行われる可能性やタイミングについて想定することも必要です。 また、アプリケーションで複数の接続が必要になる場合もあります。  
  
## <a name="see-also"></a>参照  
 [SQL Server &#40;ODBC&#41; と通信します。](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
