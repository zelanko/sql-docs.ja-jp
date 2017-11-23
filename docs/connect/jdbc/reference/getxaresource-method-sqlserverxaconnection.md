---
title: "getXAResource メソッド (SQLServerXAConnection) |Microsoft ドキュメント"
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
apiname: SQLServerXAConnection.getXAResource
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60863941867d01d2a9be0d492524c00357fbf002
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getxaresource-method-sqlserverxaconnection"></a>getXAResource メソッド (SQLServerXAConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  取得、 [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)これを管理するトランザクション マネージャーが使用するオブジェクト[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)オブジェクトの分散トランザクションへの参加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## <a name="return-value"></a>戻り値  
 XAResource オブジェクト。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この getXAResource メソッドは、javax.sql.XAConnection インターフェイスの getXAResource メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAConnection メソッド](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [SQLServerXAConnection のメンバー](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [SQLServerXAConnection クラス](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
