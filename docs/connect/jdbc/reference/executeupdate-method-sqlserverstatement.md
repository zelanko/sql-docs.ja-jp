---
title: "executeUpdate メソッド (SQLServerStatement) |Microsoft ドキュメント"
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
apiname: SQLServerStatement.executeUpdate
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 10ae662a-ce3c-4b24-875c-5c2df319d93b
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8c0c1f5238ece3adb72f108061742034b3df159f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="executeupdate-method-sqlserverstatement"></a>executeUpdate メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された SQL ステートメントを実行します。ステートメントは INSERT、UPDATE、DELETE、または SQL DDL ステートメントのような何も返さない SQL ステートメントが可能です。 以降で[!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 では、executeUpdate は正しい数のマージ操作で更新された行を返すはします。  
  
## <a name="overload-list"></a>オーバーロードの一覧  
  
|名前|Description|  
|----------|-----------------|  
|[executeUpdate (java.lang.String)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-sqlserverstatement.md)|渡された SQL ステートメントを実行します。ステートメントは INSERT、UPDATE、DELETE、MERGE、または SQL DDL ステートメントのような何も返さない SQL ステートメントが可能です。|  
|[executeUpdate (java.lang.String, int)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-int.md)|指定された SQL ステートメントと信号の実行、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]かどうかを指定したフラグでは、これによって生成される自動生成キー [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを取得を可能にする必要があります。|  
|[executeUpdate (java.lang.String、int & #91、&#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string.md)|渡された SQL ステートメントを実行し、渡された配列に示される自動生成キーを検索可能にするように、JDBC ドライバーに通知します。|  
|[executeUpdate (java.lang.String、java.lang.String & #91、&#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-java-lang-string.md)|渡された SQL ステートメントを実行し、渡された配列に示される自動生成キーを検索可能にするように、JDBC ドライバーに通知します。|  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
