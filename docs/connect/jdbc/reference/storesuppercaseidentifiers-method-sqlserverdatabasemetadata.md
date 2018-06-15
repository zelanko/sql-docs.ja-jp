---
title: storesUpperCaseIdentifiers メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesUpperCaseIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a622b748-d10b-4f02-afe3-fba4a5bca17b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16a32c65682c651c5b8fd6469501666afaf0f2bd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32847467"
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
  
  
