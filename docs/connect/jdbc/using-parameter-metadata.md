---
title: "パラメーターのメタデータを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d50af4d0d22d6042230fed2ee6b989fb7c53408d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-parameter-metadata"></a>パラメーターのメタデータの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  クエリに、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)または[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)オブジェクトで含まれているパラメーターについて、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を実装する、 [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md)クラスです。 このクラスには、単一値の形式で情報を返すフィールドおよびメソッドが多数存在します。  
  
 SQLServerParameterMetaData オブジェクトを作成する際、 [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) SQLServerPreparedStatement クラスおよび SQLServerCallableStatement クラスのメソッドです。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが関数に渡された、SQLServerCallableStatement クラスの getParameterMetaData メソッドを使用して、SQLServerParameterMetaData オブジェクト、およびさまざまなしを返すSQLServerParameterMetaData オブジェクトのメソッドを使用して、HumanResources.uspUpdateEmployeeHireInfo ストアド プロシージャ内に含まれているパラメーターのモードと型に関する情報を表示できます。  
  
 [!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  
    
> [!NOTE]  
準備されたステートメントでは、SQLServerParameterMetaData クラスを使用する場合は、いくつかの制限があります。 
**Microsoft JDBC Driver 6.0 (またはそれ以上) for SQL Server**: JDBC ドライバーでは、これらのステートメントにサブクエリや結合が含まれていない限り、SELECT、DELETE、INSERT、および UPDATE ステートメントがサポートしている SQL Server 2008 または 2008 R2 を使用する場合。 クエリのマージもサポートされていません SQLServerParameterMetaData クラスの SQL Server 2008 または 2008 R2 を使用する場合。 SQL Server 2012 以降のバージョンの場合、複雑なクエリを持つパラメーター メタデータがサポートされます。 暗号化された列のパラメーター メタデータの取得はサポートされていません。 **Microsoft JDBC Driver 4.0、4.1 や 4.2 for SQL Server で**:、JDBC ドライバーは、これらのステートメントにサブクエリや結合が含まれていない限り、SELECT、DELETE、INSERT、および UPDATE ステートメントをサポートしています。 クエリのマージもサポートされていません SQLServerParameterMetaData クラス。  

## <a name="see-also"></a>参照  
 [JDBC ドライバーによるメタデータの処理](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  

