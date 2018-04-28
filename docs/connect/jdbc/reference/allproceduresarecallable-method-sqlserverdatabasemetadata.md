---
title: allProceduresAreCallable メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
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
- SQLServerDatabaseMetaData.allProceduresAreCallable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8886137d-455e-497c-afea-4b326eda52f1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33a46aff5fde01bdc059fb2161571323c3a42285
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="allproceduresarecallable-method-sqlserverdatabasemetadata"></a>allProceduresAreCallable メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在のユーザーがによって返されるすべてのプロシージャを呼び出すアクセス許可を持っているかどうかを取得、 [getProcedures](../../../connect/jdbc/reference/getprocedures-method-sqlserverdatabasemetadata.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean allProceduresAreCallable()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**ユーザーは、すべてのプロシージャを呼び出すアクセス許可を持っている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この allProceduresAreCallable メソッドは、java.sql.DatabaseMetaData インターフェイスの allProceduresAreCallable メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
