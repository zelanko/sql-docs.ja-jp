---
title: ODBC でのトランザクション |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 093eae04962409b5ac426713aedc74aa1bd0703b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303673"
---
# <a name="performing-transactions-in-odbc"></a>ODBC でのトランザクションの実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC のトランザクションは接続レベルで管理されます。 アプリケーションはトランザクションの完了時に、その接続のすべてのステートメント ハンドルで完了したすべての作業を、コミットまたはロールバックします。 トランザクションをコミットまたはロールバックするには、アプリケーションは COMMIT ステートメントまたは ROLLBACK ステートメントを実行せずに[SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md)を呼び出す必要があります。  
  
 アプリケーションは、トランザクションを管理する 2 つの ODBC モードを切り替えるために[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)を呼び出します。  
  
-   自動コミット モード  
  
     各ステートメントは、正常に完了したときに自動的にコミットされます。 自動コミット モードで実行するときは、他のトランザクション管理関数は必要ありません。  
  
-   手動コミット モード  
  
     実行されたすべてのステートメントは、 **SQLEndTran**を呼び出して特に停止されるまで、同じトランザクションに含まれます。  
  
 自動コミット モードは、ODBC の既定のトランザクション モードです。 接続が確立されると、自動コミット モードをオフに設定して手動コミット モードに切り替えるために**SQLSetConnectAttr**が呼び出されるまで、接続は自動コミット モードになります。 アプリケーションが自動コミットを無効にすると、次にデータベースに送信されるステートメントでトランザクションが開始されます。 その後、アプリケーションが SQL_COMMIT オプションまたはSQL_ROLLBACK オプションを指定して**SQLEndTran**を呼び出すまで、トランザクションは有効です。 **SQLEndTran**が次のトランザクションを開始した後にデータベースに送信されるコマンド。  
  
 手動コミット モードから自動コミット モードに切り替えると、ドライバーは接続で現在開かれているすべてのトランザクションをコミットします。  
  
 ODBC アプリケーションで BEGIN TRANSACTION、COMMIT TRANSACTION、ROLLBACK TRANSACTION などの Transact-SQL トランザクション ステートメントを使用すると、ドライバーの動作が不確定になる可能性があるので、このような Transact-SQL トランザクション ステートメントは使用しないでください。 ODBC アプリケーションは、自動コミット モードで実行し、トランザクション管理機能またはステートメントを使用しないか、手動コミット モードで実行し、ODBC **SQLEndTran**関数を使用してトランザクションをコミットまたはロールバックする必要があります。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;トランザクションの実行](https://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
