---
title: isClosed メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
ms.assetid: 6081aa34-fc88-4dd0-9a3f-05e8488219dc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c49e7ed6e32576bf1184c024eedeac96a8b5a340
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="isclosed-method-sqlserverresultset"></a>isClosed メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  示すかどうかこの[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトが閉じられました。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**この[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトが閉じられて、 **false**がまだ開いている場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isClosed メソッドは、java.sql.ResultSet インターフェイスの isClosed メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
