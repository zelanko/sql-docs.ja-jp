---
title: JDBC ドライバーでセットの結果の管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70998fad7f3fa628b952e54a5d5dbb6cb90afde9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
|[カーソルの種類について](../../connect/jdbc/understanding-cursor-types.md)|さまざまな説明されるカーソルの種類、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]をサポートしています。|  
|[同時実行制御について](../../connect/jdbc/understanding-concurrency-control.md)|JDBC ドライバーが同時実行制御をサポートするしくみについて説明します。|  
|[行ロックについて](../../connect/jdbc/understanding-row-locking.md)|JDBC ドライバーが行ロックをサポートするしくみについて説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
