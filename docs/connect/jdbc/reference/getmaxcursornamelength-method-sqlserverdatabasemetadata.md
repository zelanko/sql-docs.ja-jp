---
title: "getMaxCursorNameLength メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.getMaxCursorNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2cd2bed9-adf4-4bcd-ae5a-d0e3428bc709
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 230ed7a8e380fb9da5c1100be02b9e4ec012d137
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getmaxcursornamelength-method-sqlserverdatabasemetadata"></a>getMaxCursorNameLength メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースで許容されるカーソル名の最大文字数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxCursorNameLength()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**許可される文字の最大数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxCursorNameLength メソッドは、java.sql.DatabaseMetaData インターフェイスの getMaxCursorNameLength メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

