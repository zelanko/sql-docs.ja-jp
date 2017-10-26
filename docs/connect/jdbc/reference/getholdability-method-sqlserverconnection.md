---
title: "getHoldability メソッド (SQLServerConnection) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.getHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b1644791-c36a-4837-86c4-9299537ee1c2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a2af3571c34946bdc494d6443b868a43f81ac1e6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getholdability-method-sqlserverconnection"></a>getHoldability メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在の保持機能を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これを使用して作成されたオブジェクト[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**保持機能レベルは次のいずれかを含む値です。  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getHoldability メソッドは、java.sql.Connection インターフェイスの getHoldability メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

