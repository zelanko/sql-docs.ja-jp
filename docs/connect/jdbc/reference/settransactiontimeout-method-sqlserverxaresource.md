---
title: "settransactiontimeout Method メソッド (SQLServerXAResource) |Microsoft ドキュメント"
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
- SQLServerXAResource.setTransactionTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38bf4a1a-6ad3-437c-b9ed-8792ab6dde7e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d2bcc25cfb09d40df95029f0c9d36e38e9658725
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="settransactiontimeout-method-sqlserverxaresource"></a>setTransactionTimeout Method メソッド (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在のトランザクション タイムアウト値を設定[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean setTransactionTimeout(int seconds)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *seconds*  
  
 **Int**値。  
  
## <a name="return-value"></a>戻り値  
 **true**場合は、タイムアウトが正常に設定します。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>解説  
 この setTransactionTimeout メソッドは、javax.transaction.xa.XAResource インターフェイスの setTransactionTimeout メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のメソッド](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource クラス](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  

