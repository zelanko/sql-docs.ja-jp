---
title: ODBC でのトランザクション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc91460599df7fff2bed9c7a7a20991b8bae3b57
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425671"
---
# <a name="transactions-in-odbc"></a>ODBC でのトランザクション
  ODBC のトランザクションは接続レベルで管理されます。 アプリケーションはトランザクションの完了時に、その接続のすべてのステートメント ハンドルで完了したすべての作業を、コミットまたはロールバックします。 トランザクションをロールバックまたはコミットは、アプリケーションを呼び出す必要があります[SQLEndTran](../../native-client-odbc-api/sqlendtran.md) COMMIT または ROLLBACK ステートメントを送信する代わりにします。  
  
 アプリケーションを呼び出す[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)トランザクションの管理の 2 つの ODBC モードを切り替えます。  
  
-   自動コミット モード  
  
     各ステートメントは、正常に完了したときに自動的にコミットされます。 自動コミット モードで実行するときは、他のトランザクション管理関数は必要ありません。  
  
-   手動コミット モード  
  
     具体的には呼び出すことによって停止されるまで、同じトランザクション内で実行されるすべてのステートメントが含まれる**SQLEndTran**します。  
  
 自動コミット モードは、ODBC の既定のトランザクション モードです。 まで自動コミット モードでは、接続が行われたときに**SQLSetConnectAttr**を自動コミット モードの設定で手動コミット モードに切り替えると呼びます。 アプリケーションが自動コミットを無効にすると、次にデータベースに送信されるステートメントでトランザクションが開始されます。 その後、トランザクションがアプリケーション呼び出しまで有効になります**SQLEndTran**した状態または SQL_ROLLBACK オプションを使用します。 後のデータベースに送信されたコマンド**SQLEndTran**次のトランザクションが開始されます。  
  
 手動コミット モードから自動コミット モードに切り替えると、ドライバーは接続で現在開かれているすべてのトランザクションをコミットします。  
  
 ODBC アプリケーションで BEGIN TRANSACTION、COMMIT TRANSACTION、ROLLBACK TRANSACTION などの Transact-SQL トランザクション ステートメントを使用すると、ドライバーの動作が不確定になる可能性があるので、このような Transact-SQL トランザクション ステートメントは使用しないでください。 ODBC アプリケーションする必要があります自動コミット モードで実行しないトランザクション管理関数またはステートメントを使用して、または手動コミット モードで実行を使用、ODBC **SQLEndTran**トランザクションをロールバックまたはコミットする関数。  
  
## <a name="see-also"></a>参照  
 [トランザクションを実行する&#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
