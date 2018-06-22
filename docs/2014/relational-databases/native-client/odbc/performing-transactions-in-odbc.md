---
title: ODBC でのトランザクション |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b146a3f4a3331ddcfc7606825a0300b986f1a116
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073955"
---
# <a name="transactions-in-odbc"></a>ODBC でのトランザクション
  ODBC のトランザクションは接続レベルで管理されます。 アプリケーションはトランザクションの完了時に、その接続のすべてのステートメント ハンドルで完了したすべての作業を、コミットまたはロールバックします。 アプリケーションを呼び出す必要がありますをコミットまたはロールバック、トランザクション、 [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) COMMIT または ROLLBACK ステートメントを送信する代わりにします。  
  
 アプリケーションが呼び出す[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)トランザクションを管理するための 2 つの ODBC モードを切り替えます。  
  
-   自動コミット モード  
  
     各ステートメントは、正常に完了したときに自動的にコミットされます。 自動コミット モードで実行するときは、他のトランザクション管理関数は必要ありません。  
  
-   手動コミット モード  
  
     具体的には呼び出すことによって停止されるまで、同じトランザクションで実行されるすべてのステートメントが含まれて**SQLEndTran**です。  
  
 自動コミット モードは、ODBC の既定のトランザクション モードです。 までの自動コミット モードでは、接続が行われたときに**SQLSetConnectAttr**を自動コミット モードの設定で手動コミット モードに切り替えると呼びます。 アプリケーションが自動コミットを無効にすると、次にデータベースに送信されるステートメントでトランザクションが開始されます。 その後、トランザクションは、アプリケーションが有効になります**SQLEndTran**指定してまたは SQL_ROLLBACK オプションを使用します。 後のデータベースに送られたコマンド**SQLEndTran**次のトランザクションを開始します。  
  
 手動コミット モードから自動コミット モードに切り替えると、ドライバーは接続で現在開かれているすべてのトランザクションをコミットします。  
  
 ODBC アプリケーションで BEGIN TRANSACTION、COMMIT TRANSACTION、ROLLBACK TRANSACTION などの Transact-SQL トランザクション ステートメントを使用すると、ドライバーの動作が不確定になる可能性があるので、このような Transact-SQL トランザクション ステートメントは使用しないでください。 ODBC アプリケーション自動コミット モードで実行およびされませんを使用、トランザクション管理関数やステートメント、または手動コミット モードで実行し、ODBC **SQLEndTran**コミットまたはトランザクションをロールバックする関数。  
  
## <a name="see-also"></a>参照  
 [トランザクションを実行する&#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  