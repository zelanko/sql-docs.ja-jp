---
title: "supportsMixedCaseQuotedIdentifiers メソッド |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.supportsMixedCaseQuotedIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 76c68fc2-5af6-4b8d-baee-245716fdc5cc
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a993470e0c2f7754d3940193fe531d5966312f2f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="supportsmixedcasequotedidentifiers-method-sqlserverdatabasemetadata"></a>supportsMixedCaseQuotedIdentifiers メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  引用符で囲まれた大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別して扱うかどうか、およびそれらの識別子を大文字小文字混在で格納するかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsMixedCaseQuotedIdentifiers()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**識別子が大文字小文字混在で格納されている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsMixedCaseQuotedIdentifiers メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsMixedCaseQuotedIdentifiers メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
