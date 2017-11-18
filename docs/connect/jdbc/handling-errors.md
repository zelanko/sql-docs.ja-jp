---
title: "エラー処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cfcb29aa70f9bfb56c793f6fa5d1d8b31d45f8bf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="handling-errors"></a>エラーの処理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  使用する場合、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、すべてのデータベース エラー状態は、例外として Java アプリケーションに返される、 [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md)クラスです。 SQLServerException クラスの次のメソッドは、java.sql.SQLException および java.lang.Throwable; から継承されます。特定の情報を返すに使用されることがあると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]発生したエラー。  
  
-   getSQLState は、標準的な x/open または SQL99 状態コードの例外を返します。  
  
-   getErrorCode では、特定のデータベース エラー番号を返します。  
  
-   getMessage では、例外の全文を返します。 エラー メッセージ テキストは問題について説明します。そして、オブジェクト名のような情報のプレースホルダーを含むことがよくあります。こうしたプレースホルダーは、エラー メッセージが表示されるとき、その中に挿入されます。  
  
-   返す例外オブジェクトがある場合は、getNextException、SQLServerException の次のオブジェクトまたは null を返します。  
  
 次の例では、開いている接続を[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが関数に渡され、FROM 句がない不適切な SQL ステートメントが構築されます。 次に、ステートメントが実行され、SQL 例外が処理されます。  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーに関する問題の診断](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  

