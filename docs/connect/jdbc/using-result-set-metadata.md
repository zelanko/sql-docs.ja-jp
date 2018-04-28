---
title: 結果セットの使用メタデータ |Microsoft ドキュメント
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
ms.topic: article
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 03e6d7d247474c5c5c216ce744591e58f1c0eec8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-result-set-metadata"></a>結果セットのメタデータの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  結果セットが含まれている列に関する情報を照会する、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を実装する、 [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)クラスです。 このクラスには、単一値の形式で情報を返すメソッドが多数存在します。  
  
 SQLServerResultSetMetaData オブジェクトを作成する際、 [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが関数に渡された、SQLServerResultSet クラスの getMetaData メソッドは、SQLServerResultSetMetaData オブジェクトとのさまざまなメソッドを返すために使用しますSQLServerResultSetMetaData オブジェクトを使用して、結果セットに含まれる列の名前とデータ型に関する情報を表示します。  
  
 [!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによるメタデータの処理](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  
