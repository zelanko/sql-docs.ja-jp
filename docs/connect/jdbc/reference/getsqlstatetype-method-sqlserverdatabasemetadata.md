---
title: getSQLStateType メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 55079e30c2f8908153cc708aca699e77aef41261
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66774182"
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>getSQLStateType メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  SQLException.getSQLState メソッドによって返される SQLSTATE が、X/Open (現在は Open Group)、SQL CLI、SQL99 (JDBC 3.0)、SQL:2003 (JDBC 4.0) のいずれであるかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>戻り値  
 SQLSTATE の種類を示す **int** です。次のいずれかの値になります。  
  
-   Java ランタイム環境バージョン 5.0: 場合、 **xopenStates**接続プロパティに設定されて**true**DatabaseMetaData.sqlStateXOpen を返します。 それ以外の場合、DatabaseMetaData.sqlStateSQL99 します。  
  
-   Java ランタイム環境バージョン 6.0: 場合、 **xopenStates**接続プロパティに設定されて**true**DatabaseMetaData.sqlStateXOpen を返します。 それ以外の場合、DatabaseMetaData.sqlStateSQL します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getSQLStateType メソッドは、java.sql.DatabaseMetaData インターフェイスで getSQLStateType メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
