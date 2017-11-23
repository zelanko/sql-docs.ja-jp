---
title: "rollback メソッド () |Microsoft ドキュメント"
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
apiname: SQLServerConnection.rollback ()
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 7adb6772-4047-4d8e-931d-b3d20eec44b5
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 384d2cac20f8764daa7cbcee2803f56f9a79a625
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="rollback-method-"></a>rollback () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在のトランザクションで行われたすべての変更が取り消され、これによって現在保持されているデータベース ロックは解放[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void rollback()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 このロールバック メソッドは、java.sql.Connection インターフェイスの rollBack メソッドによって指定されます。  
  
 このメソッドは、自動コミット モードが無効になっている場合にのみ使用してください。  
  
## <a name="see-also"></a>参照  
 [rollback メソッド &#40;です。SQLServerConnection &#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
