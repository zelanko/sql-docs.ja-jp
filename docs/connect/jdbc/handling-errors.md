---
title: エラーの処理 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eee315022a94795dd27ae8ae7fee6cc784912bec
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786113"
---
# <a name="handling-errors"></a>エラーの処理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] の使用時に発生するデータベース エラー状態はすべて、[SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md) クラスの例外として Java アプリケーションに返されます。 SQLServerException クラスの次のメソッドは、java.sql.SQLException および java.lang.Throwable から継承されます。これらのメソッドを使用して、発生した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーに関する特定の情報を返すことができます。  
  
-   getSQLState は、例外の標準的な X/Open または SQL99 状態コードが返されます。  
  
-   getErrorCode は、具体的なデータベース エラー番号が返されます。  
  
-   getMessage は、例外の全文が返されます。 エラー メッセージ テキストは問題について説明します。そして、オブジェクト名のような情報のプレースホルダーを含むことがよくあります。こうしたプレースホルダーは、エラー メッセージが表示されるとき、その中に挿入されます。  
  
-   返す例外オブジェクトがある場合は、getNextException、SQLServerException の次のオブジェクトまたは null を返します。  
  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続が関数に渡され、FROM 句のない不適切な SQL ステートメントが作成されます。 次に、ステートメントが実行され、SQL 例外が処理されます。  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーで発生した問題の診断](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
