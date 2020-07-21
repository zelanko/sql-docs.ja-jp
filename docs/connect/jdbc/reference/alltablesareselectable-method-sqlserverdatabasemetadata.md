---
title: allTablesAreSelectable メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4fbd5a1d132bdb1e0d661e05968709ed604006d9
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922917"
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
  
## <a name="remarks"></a>解説  
 この allTablesAreSelectable メソッドは、java.sql.DatabaseMetaData インターフェイスの allTablesAreSelectable メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
