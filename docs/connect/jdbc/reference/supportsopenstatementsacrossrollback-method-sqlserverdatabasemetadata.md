---
title: supportsOpenStatementsAcrossRollback メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsOpenStatementsAcrossRollback
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4e38b938-f39f-4c5d-9b32-4ba489535c45
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ee68785233d81b69548ffa07a5f6e9cb204d34e5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66763947"
---
# <a name="supportsopenstatementsacrossrollback-method-sqlserverdatabasemetadata"></a>supportsOpenStatementsAcrossRollback メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが複数のロールバックにわたってステートメントが開いたままの状態をサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsOpenStatementsAcrossRollback()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsOpenStatementsAcrossRollback メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsOpenStatementsAcrossRollback メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
