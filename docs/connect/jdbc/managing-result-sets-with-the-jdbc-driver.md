---
title: "JDBC ドライバーでセットの結果の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e17e39f8a83313a60b269fed82631b80f07ffed5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>JDBC ドライバーによる結果セットの管理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  結果セットは、データ ソースから (通常はクエリの結果として) 返された一連のデータを表すオブジェクトです。 結果セットは要求されたデータ要素を保持するための行と列を含み、移動にはカーソルを使用します。 結果セットは更新できます。つまり、変更し、変更内容を元のデータ ソースに反映することができます。 また、結果セットには、基になるデータ ソースの変更に対するさまざまなレベルの応答性を設定できます。  
  
 ステートメントの作成時に、これを呼び出すときに、結果セットの種類が決定されます、 [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスが行われます。 結果セットの基本的な役割は、データベースのデータの使用可能な表現を Java アプリケーションに提供することです。 これは通常、結果セットのデータ要素に対する型指定された getter メソッドと setter メソッドによって行われます。  
  
 次の例では、これに基づいて、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースを呼び出すことによっては結果セットの作成、 [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。 使用して、結果セットからデータが表示されます、 [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 このセクションのトピックでは、結果セットの使用について、カーソルの種類、同時実行、行ロックなどのさまざまな側面から説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[カーソルの種類をについてください。](../../connect/jdbc/understanding-cursor-types.md)|さまざまな説明されるカーソルの種類、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]をサポートしています。|  
|[同時実行制御をについてください。](../../connect/jdbc/understanding-concurrency-control.md)|JDBC ドライバーが同時実行制御をサポートするしくみについて説明します。|  
|[行ロックについてください。](../../connect/jdbc/understanding-row-locking.md)|JDBC ドライバーが行ロックをサポートするしくみについて説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
