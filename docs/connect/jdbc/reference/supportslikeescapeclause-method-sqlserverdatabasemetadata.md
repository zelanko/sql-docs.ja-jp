---
title: supportsLikeEscapeClause メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsLikeEscapeClause
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cfb43430-88bf-4386-847a-10ea1e5ce7db
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 587dbb2e00782b1549a643a1c171bd75867e761b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66764330"
---
# <a name="supportslikeescapeclause-method-sqlserverdatabasemetadata"></a>supportsLikeEscapeClause メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが LIKE エスケープ句の指定をサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsLikeEscapeClause()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsLikeEscapeClause メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsLikeEscapeClause メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
