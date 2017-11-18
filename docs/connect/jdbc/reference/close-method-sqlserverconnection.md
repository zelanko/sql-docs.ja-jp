---
title: "close メソッド (SQLServerConnection) |Microsoft ドキュメント"
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
- SQLServerConnection.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0f26585-bdf7-4737-b434-8c7e115c8e94
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e9f7dc84edb37bde6242be79830198ab565547e0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="close-method-sqlserverconnection"></a>close メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このリリース[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトのデータベースと JDBC リソースを待たずにすぐに自動的に解放します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 このメソッドは、java.sql.Connection インターフェイスの close メソッドによって指定されます。  
  
 トランザクションの途中で close メソッドを呼び出すと、トランザクションのロールバックとします。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

