---
title: supportsCorrelatedSubqueries メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsCorrelatedSubqueries
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85bb1bcc-31ae-4f6b-a103-699724bbb0aa
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f722d457bd56184df4d8dea3e0616e7a4370c94d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794211"
---
# <a name="supportscorrelatedsubqueries-method-sqlserverdatabasemetadata"></a>supportsCorrelatedSubqueries メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが、相関サブクエリをサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsCorrelatedSubqueries()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsCorelatedSubqueries メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsCorelatedSubqueries メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
