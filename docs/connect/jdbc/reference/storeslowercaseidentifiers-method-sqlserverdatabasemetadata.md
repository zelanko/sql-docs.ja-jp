---
title: storesLowerCaseIdentifiers メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesLowerCaseIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b7dd60f5-c4f3-4b14-9a33-d95327395083
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10a0bc171ca6f31070464471baea496331e550e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771390"
---
# <a name="storeslowercaseidentifiers-method-sqlserverdatabasemetadata"></a>storesLowerCaseIdentifiers メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  引用符で囲まれていない大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を小文字で格納するかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean storesLowerCaseIdentifiers()  
```  
  
## <a name="return-value"></a>戻り値  
 識別子を小文字で格納する場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この storesLowerCaseIdentifiers メソッドは、java.sql.DatabaseMetaData インターフェイスで storesLowerCaseIdentifiers メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
