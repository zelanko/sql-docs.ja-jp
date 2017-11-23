---
title: "データベースのメタデータを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 96dea7d43571c4a1e23f8757221af7cfab7a561c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="using-database-metadata"></a>データベースのメタデータの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  サポート内容に関する情報をデータベースに照会する、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を実装する、 [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)クラスです。 このクラスには、単一値形式または結果セットとして情報を返すメソッドが多数存在します。  
  
 SQLServerDatabaseMetaData オブジェクトを作成する際、 [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスに接続されているデータベースに関する情報を取得します。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが関数に渡された、SQLServerDatabaseMetadata オブジェクトとのさまざまなメソッドを返す、SQLServerConnection クラスの getMetaData メソッドを使用しますSQLServerDatabaseMetaData オブジェクトを使用して、ドライバー、ドライバーのバージョン、データベース名、およびデータベースのバージョンに関する情報を表示します。  
  
 [!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによるメタデータの処理](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  
