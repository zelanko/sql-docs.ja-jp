---
title: "setObject メソッド (SQLServerCallableStatement) |Microsoft ドキュメント"
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
apiname: SQLServerCallableStatement.setObject
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 7110f6c5-4af3-4b50-a4d4-1bae1876c70d
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 77f3add6ad521d097dccc09a801db3acf9bb37a3
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setobject-method-sqlservercallablestatement"></a>setObject メソッド (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定したオブジェクトを使用して、指定されたパラメーターの値を設定します。  
  
 以降で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 では、このメソッドの動作は、によって変更が、 **sendTimeAsDatetime**接続プロパティ ([接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)) および[SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)です。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。  
  
## <a name="overload-list"></a>オーバーロードの一覧  
  
|名前|Description|  
|----------|-----------------|  
|[setObject (java.lang.String, java.lang.Object)](../../../connect/jdbc/reference/setobject-method-java-lang-string-java-lang-object.md)|指定したオブジェクトを使用して、指定されたパラメーターの値を設定します。|  
|[setObject (java.lang.String、java.lang.Object, int)](../../../connect/jdbc/reference/setobject-method-java-lang-string-java-lang-object-int.md)|渡されたオブジェクトと変換先の型を使用して、指定されたパラメーターの値を設定します。|  
|[setObject (java.lang.String、java.lang.Object、int, int)](../../../connect/jdbc/reference/setobject-method-java-lang-string-java-lang-object-int-int.md)|渡されたオブジェクト、変換先の型、および小数点以下桁数を使用して、指定されたパラメーターの値を設定します。|  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
