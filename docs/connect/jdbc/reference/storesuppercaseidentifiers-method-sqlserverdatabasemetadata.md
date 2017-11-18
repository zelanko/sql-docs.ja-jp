---
title: "storesUpperCaseIdentifiers メソッド |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.storesUpperCaseIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a622b748-d10b-4f02-afe3-fba4a5bca17b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bbd1d80d48351719b5c412039a424fd4caaf80ed
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="storesuppercaseidentifiers-method-sqlserverdatabasemetadata"></a>storesUpperCaseIdentifiers メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  引用符で囲まれていない大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を大文字で格納するかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean storesUpperCaseIdentifiers()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**識別子が大文字で格納されている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この storesUpperCaseIdentifiers メソッドは、java.sql.DatabaseMetaData インターフェイスの storesUpperCaseIdentifiers メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

