---
title: supportsMultipleResultSets メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsMultipleResultSets
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cb4d0b91-db1d-4a6f-a87c-8ea125215afc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c6abf07e5ff18fba6fd68e8c109388f82bc5eae4
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66764140"
---
# <a name="supportsmultipleresultsets-method-sqlserverdatabasemetadata"></a>supportsMultipleResultSets メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) クラスの [execute](../../../connect/jdbc/reference/execute-method.md) メソッドへの 1 回の呼び出しから複数の [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトを取得することを、データベースがサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsMultipleResultSets()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsMultipleResultSets メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsMultipleResultSets メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
