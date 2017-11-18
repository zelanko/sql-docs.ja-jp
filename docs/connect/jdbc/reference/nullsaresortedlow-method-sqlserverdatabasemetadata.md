---
title: "nullsAreSortedLow メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.nullsAreSortedLow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 30c06a9d-3513-42d0-8b2a-5a20ac31eb0e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d473f238ca3ae4a414324afe33745ac295fe9f2c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="nullsaresortedlow-method-sqlserverdatabasemetadata"></a>nullsAreSortedLow メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  NULL 値が下位に並べ替えられるかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean nullsAreSortedLow()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**値が下位に並べ替えられる場合です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この nullsAreSortedLow メソッドは、java.sql.DatabaseMetaData インターフェイスの nullsAreSortedLow メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

