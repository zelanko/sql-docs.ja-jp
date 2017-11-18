---
title: "isClosed メソッド (SQLServerConnection) |Microsoft ドキュメント"
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
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 634a402f06005c7235755988adf1435d38da0313
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  示すかどうかこの[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトが閉じられました。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**接続が閉じる場合**false**されていない場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isClosed メソッドは、java.sql.Connection インターフェイスの isClosed メソッドによって指定されます。  
  
 呼び出された SQLServerConnection オブジェクトの状態を確認します。 場合、接続が閉じられて、[閉じる](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)メソッドが呼び出された、または特定の致命的なエラーが発生した場合。 このメソッドは**true**のみを呼び出す際 close メソッドが呼び出された後にします。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

