---
title: isClosed メソッド (SQLServerStatement) |Microsoft ドキュメント
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
ms.assetid: e79b5b53-16b0-42a3-be4e-542a77a21e12
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c597e8175ce7a5119735da0f13cf1afc82048228
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="isclosed-method-sqlserverstatement"></a>isClosed メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  示すかどうかこの[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトが閉じられました。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**この[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトが閉じられて、 **false**がまだ開いている場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isClosed メソッドは、java.sql.Statement インターフェイスの isClosed メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
