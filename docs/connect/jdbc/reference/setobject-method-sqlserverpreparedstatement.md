---
title: "setObject メソッド (SQLServerPreparedStatement) |Microsoft ドキュメント"
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
apiname:
- SQLServerPreparedStatement.setObject
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 93a2b22c-82b4-48c7-a428-369ebe98a372
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4582f5f5ea56938562570a1b5e01393fa77de76a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setobject-method-sqlserverpreparedstatement"></a>setObject メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたオブジェクトを使用して、指定されたパラメーターの値を設定します。  
  
 以降で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 では、このメソッドの動作は、によって変更が、 **sendTimeAsDatetime**接続プロパティ ([接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)) および[SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)です。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。  
  
## <a name="overload-list"></a>オーバーロードの一覧  
  
|名前|Description|  
|----------|-----------------|  
|[setObject (int, java.lang.Object)](../../../connect/jdbc/reference/setobject-method-int-java-lang-object.md)|渡されたオブジェクトを使用して、指定されたパラメーターの値を設定します。|  
|[setObject (int、java.lang.Object, int)](../../../connect/jdbc/reference/setobject-method-int-java-lang-object-int.md)|指定したオブジェクトとターゲットの型を使用して、指定されたパラメーターの値を設定します。|  
|[setObject (int、java.lang.Object、int, int)](../../../connect/jdbc/reference/setobject-method-int-java-lang-object-int-int.md)|指定したオブジェクト、ターゲットの種類、および小数点以下桁数を使用して、指定されたパラメーターの値を設定します。|  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

