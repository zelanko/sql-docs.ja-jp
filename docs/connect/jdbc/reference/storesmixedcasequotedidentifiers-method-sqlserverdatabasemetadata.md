---
title: storesMixedCaseQuotedIdentifiers メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesMixedCaseQuotedIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1ffa599c-d0c8-43b6-8e9b-7c856a846630
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a997de47a565879009b5a21635bc61586f04e1d0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838480"
---
# <a name="storesmixedcasequotedidentifiers-method-sqlserverdatabasemetadata"></a>storesMixedCaseQuotedIdentifiers メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  引用符で囲まれた大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を大文字小文字混在で格納するかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean storesMixedCaseQuotedIdentifiers()  
```  
  
## <a name="return-value"></a>戻り値  
 識別子を大文字小文字混在で格納する場合は  です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この storesMixedCaseQuotedIdentifiers メソッドは、java.sql.DatabaseMetaData インターフェイスで storesMixedCaseQuotedIdentifiers メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
