---
title: allTablesAreSelectable メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.allTablesAreSelectable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb340450-45a7-49c8-84bc-1b9dd5ee842f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fbc609140cf15e90e409cf123f59ae3409d15a26
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803686"
---
# <a name="alltablesareselectable-method-sqlserverdatabasemetadata"></a>allTablesAreSelectable メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在のユーザーが、[getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md) メソッドで返されたすべてのテーブルを SELECT ステートメントで使用するアクセス許可を持っているかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean allTablesAreSelectable()  
```  
  
## <a name="return-value"></a>戻り値  
 ユーザーがすべてのテーブルを使用するためのアクセス許可を持っている場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この allTablesAreSelectable メソッドは、java.sql.DatabaseMetaData インターフェイスで allTablesAreSelectable メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
