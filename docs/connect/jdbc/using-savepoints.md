---
title: セーブポイントの使用 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72b354c805a3d46dd31f6f9df308e33493c2db2c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992934"
---
# <a name="using-savepoints"></a>セーブポイントの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  セーブポイントは、トランザクションを部分的にロールバックするメカニズムです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] では、SAVE TRANSACTION savepoint_name ステートメントを使用してセーブポイントを作成できます。 その後 ROLLBACK TRANSACTION savepoint_name ステートメントを実行すると、トランザクションの最初にロールバックするのではなく、セーブポイントにロールバックされます。  
  
 セーブポイントは、エラーが発生する可能性が小さい状況で役立ちます。 エラーの頻度が低い場合には、セーブポイントを使用してトランザクションの一部をロールバックする方法は、更新が有効であるかどうかを更新を行う前にトランザクションごとにテストするよりも効率的です。 更新とロールバックは負荷の大きい処理です。そのため、セーブポイントが効果を発揮するのは、エラーの発生確率が低く、なおかつ更新の有効性を事前にチェックするコストの方が高い場合に限られます。  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は、[SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [setSavepoint](../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md) メソッドを通じてセーブポイントの使用をサポートします。 setSavepoint メソッドを使用することで、名前付きセーブポイントまたは名前を割り当てられていないセーブポイントを、現在のトランザクションに作成できます。またこのメソッドによって [SQLServerSavepoint](../../connect/jdbc/reference/sqlserversavepoint-class.md) オブジェクトが返されます。 セーブポイントは 1 つのトランザクションに複数作成できます。 特定のセーブポイントまでトランザクションをロールバックするには、SQLServerSavepoint オブジェクトを [rollback (java.sql.Savepoint)](../../connect/jdbc/reference/rollback-method-java-sql-savepoint.md) メソッドに渡します。  
  
 次の例では、`try` ブロック内の 2 つの個別のステートメントで構成されるローカル トランザクションの実行時にセーブポイントが使用されます。 ステートメントは [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースの Production.ScrapReason テーブルに対して実行され、2 番目のステートメントのロールバックにセーブポイントが使用されています。 この結果、最初のステートメントのみがデータベースにコミットされます。  
  
 [!code[JDBC#UsingSavepoints1](../../connect/jdbc/codesnippet/Java/using-savepoints_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーを使用したトランザクションの実行](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
