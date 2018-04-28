---
title: getType メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
apiname:
- SQLServerResultSet.getType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ffbc4a02-e851-431c-bc1a-7ab381d982bb
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bfcaf84bb9b9d941ff5b65f2e1a952997233d603
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="gettype-method-sqlserverresultset"></a>getType メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このカーソルの種類を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getType()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**を示す現在のカーソルの種類は、次の値のいずれかになります。  
  
 ResultSet.TYPE_FORWARD_ONLY  
  
 ResultSet.TYPE_SCROLL_INSENSITIVE  
  
 ResultSet.TYPE_SCROLL_SENSITIVE  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getType メソッドは、java.sql.ResultSet インターフェイスの getType メソッドによって指定されます。  
  
 このメソッドを使用すると、実際のカーソルの種類を確認できます。 アプリケーションで TYPE_FORWARD_ONLY を選択した場合、または既定のカーソルの種類を使用した場合は、TYPE_FORWARD_ONLY が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
