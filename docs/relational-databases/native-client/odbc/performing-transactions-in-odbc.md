---
title: "ODBC でのトランザクション |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2984304ae15715e5a105fa5d6b3272f518cde28
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="performing-transactions-in-odbc"></a>ODBC でトランザクションを実行します。
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC のトランザクションは接続レベルで管理されます。 アプリケーションはトランザクションの完了時に、その接続のすべてのステートメント ハンドルで完了したすべての作業を、コミットまたはロールバックします。 アプリケーションを呼び出す必要がありますをコミットまたはロールバック、トランザクション、 [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) COMMIT または ROLLBACK ステートメントを送信する代わりにします。  
  
 アプリケーションが呼び出す[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)トランザクションを管理するための 2 つの ODBC モードを切り替えます。  
  
-   自動コミット モード  
  
     各ステートメントは、正常に完了したときに自動的にコミットされます。 自動コミット モードで実行するときは、他のトランザクション管理関数は必要ありません。  
  
-   手動コミット モード  
  
     具体的には呼び出すことによって停止されるまで、同じトランザクションで実行されるすべてのステートメントが含まれて**SQLEndTran**です。  
  
 自動コミット モードは、ODBC の既定のトランザクション モードです。 までの自動コミット モードでは、接続が行われたときに**SQLSetConnectAttr**を自動コミット モードの設定で手動コミット モードに切り替えると呼びます。 アプリケーションが自動コミットを無効にすると、次にデータベースに送信されるステートメントでトランザクションが開始されます。 その後、トランザクションは、アプリケーションが有効になります**SQLEndTran**指定してまたは SQL_ROLLBACK オプションを使用します。 後のデータベースに送られたコマンド**SQLEndTran**次のトランザクションを開始します。  
  
 手動コミット モードから自動コミット モードに切り替えると、ドライバーは接続で現在開かれているすべてのトランザクションをコミットします。  
  
 ODBC アプリケーションで BEGIN TRANSACTION、COMMIT TRANSACTION、ROLLBACK TRANSACTION などの Transact-SQL トランザクション ステートメントを使用すると、ドライバーの動作が不確定になる可能性があるので、このような Transact-SQL トランザクション ステートメントは使用しないでください。 ODBC アプリケーション自動コミット モードで実行およびされませんを使用、トランザクション管理関数やステートメント、または手動コミット モードで実行し、ODBC **SQLEndTran**コミットまたはトランザクションをロールバックする関数。  
  
## <a name="see-also"></a>参照  
 [実行するトランザクション &#40; ODBC &#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
